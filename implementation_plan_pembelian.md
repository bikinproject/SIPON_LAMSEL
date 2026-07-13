## 1. Implementation Plan — Modul Pembelian (Purchase Module)

Penambahan fitur **Modul Pembelian** pada sistem Dashmo. Fitur ini bertujuan untuk mengelola transaksi pembelian barang dari pemasok, termasuk kemampuan update harga beli, perhitungan HPP (Harga Pokok Penjualan), penambahan stok, serta manajemen pembayaran berdasarkan limit kredit pemasok.

---

## 2. Arsitektur Sistem

> [!IMPORTANT]
> **Dashmo berjalan sebagai aplikasi terpisah** dengan database sendiri di sisi client. Dashmo **tidak** mengakses database Acosys secara langsung. Dashmo adalah backend API (Laravel) yang mengelola data pembelian secara mandiri.

```
┌─────────────────┐        REST API        ┌──────────────────────┐
│   Frontend /    │  ─────────────────────▶ │   Dashmo Backend     │
│   Mobile App    │ ◀─────────────────────  │   (Laravel API)      │
└─────────────────┘     JSON Response       └──────────────────────┘
                                                        │
                                                        │ Eloquent ORM
                                                        ▼
                                            ┌──────────────────────┐
                                            │  Database Client     │
                                            │  (MySQL — Acosys DB) │
                                            └──────────────────────┘
```

---

## 3. Fitur yang Diimplementasikan

### 3.1 Update Harga Beli — **Manual per Item**
- Saat harga beli di transaksi berbeda dari `product.costprice`, sistem **tidak otomatis** mengubah harga.
- User diberikan **pilihan toggle / checkbox per item** untuk memutuskan apakah harga beli akan di-update ke master produk.
- Jika diaktifkan, sistem akan update:
  - `product.costprice`, `product.netpurchase`, `product.supplier`
  - `productmanagement.costprice`, `productmanagement.netpurchase` (per divisi/departement)

### 3.2 Recalculate HPP Inventory Lama
- Jika harga beli item berubah **dan** user memilih update harga, sistem akan melakukan recalculate HPP pada inventory lama yang masuk dari transaksi pembelian yang sama (berdasarkan `reference`).
- Query yang dieksekusi:
  ```sql
  UPDATE inventory
  SET invvalue = :new_price
  WHERE reference = :purchaseid
    AND productid = :productid
    AND transid <> :purchaseid
  ```
- Ini memastikan nilai HPP di inventory konsisten dengan harga beli terbaru sebagai **referensi akuntansi**.

### 3.3 Penambahan Stok (Inventory)
- Setiap transaksi pembelian yang tersimpan otomatis menambah stok melalui insert ke tabel `inventory`.
- Field yang relevan:
  - `invin` = qty yang dibeli
  - `invout` = 0
  - `invvalue` = harga beli per unit
  - `transtype` = `1` (tipe: Pembelian)
  - `reference` = `purchaseid`

### 3.4 Pembayaran Berdasarkan Pemasok (Term of Payment & Credit Limit)

#### Term of Payment
- Sistem membaca `supplier.termofpayment` secara otomatis saat pemasok dipilih.
- Format yang didukung:
  - `"2/10, n/30"` → diskon 2% jika bayar ≤ 10 hari; jatuh tempo 30 hari
  - `"COD"` → bayar di tempat, `purchasetype = CASH`
- Field yang terisi otomatis dari parsing: `earlydiscdays`, `earlydiscvalue`, `duedays`, `duedate`.

#### Validasi Credit Limit — **Hard Block**
- Sebelum transaksi pembelian kredit disimpan, sistem menghitung total hutang yang masih outstanding ke pemasok tersebut:
  ```sql
  SELECT SUM(debit - credit) as outstanding
  FROM purchasepayments
  WHERE purchaseidref IN (
      SELECT purchaseid FROM purchase WHERE supplierid = :supplierid
  ) AND accepted = 0
  ```
- Jika `outstanding + total_transaksi_baru > supplier.creditlimit` → **transaksi di-BLOKIR**, API mengembalikan error dengan pesan yang jelas.
- Tidak ada opsi bypass tanpa persetujuan (hard block).

### 3.5 Jurnal Akuntansi Otomatis
- Setiap pembelian yang tersimpan akan **otomatis** mencatat entri jurnal ke tabel `journal` dan `journaltrans`.
- Pola jurnal:

| Akun | Debit | Kredit |
|---|---|---|
| Persediaan (Inventory Acc) | ✅ Total Pembelian | — |
| Kas / Hutang Usaha (Payable Acc) | — | ✅ Total Pembelian |

- Referensi akun diambil dari `product.inventoryacc` dan `supplier.payableacc`.

---

## 4. Komponen yang Dibangun

### 4.1 Service Layer

**`app/Services/PurchaseService.php`**

Berisi seluruh business logic. Ini adalah inti dari implementasi.

| Method | Deskripsi |
|---|---|
| `createPurchase(array $data)` | Orkestrasi seluruh proses pembelian dalam DB transaction |
| `generatePurchaseId(string $divisionId)` | Increment `division.purchaseidno` dan generate nomor transaksi |
| `validateCreditLimit(string $supplierId, float $amount)` | Validasi hard block credit limit |
| `updateProductCostPrice(string $productId, float $price, ...)` | Update `product` dan `productmanagement` |
| `recalcInventoryHpp(string $purchaseId, string $productId, float $price)` | Recalculate HPP inventory lama |
| `insertInventoryStock(array $items, string $purchaseId, ...)` | Insert baris stok masuk ke `inventory` |
| `recordPayment(string $purchaseId, array $paymentData)` | Insert ke `purchasepayments` |
| `createJournalEntry(string $purchaseId, array $journalData)` | Insert ke `journal` dan `journaltrans` |
| `parseTermOfPayment(string $term)` | Parse string `termofpayment` menjadi array terstruktur |
| `getSupplierCreditInfo(string $supplierId)` | Hitung outstanding dan sisa limit kredit |

---

### 4.2 Form Request (Validasi Input)

**`app/Http/Requests/CreatePurchaseRequest.php`**

```
Body Request:
├── supplierid          → required | exists:supplier,id
├── purchasedate        → required | date
├── purchasetype        → required | in:0,1,2  (0=CASH, 1=COD, 2=CREDIT)
├── division            → required | exists:division,id
├── departement         → required | exists:departement,id
├── memo                → nullable | string
├── items[]             → required | array | min:1
│   ├── productid           → required | exists:product,id
│   ├── qty                 → required | numeric | min:0.001
│   ├── unit                → required | exists:units,unit
│   ├── price               → required | numeric | min:0
│   ├── percentdisc         → nullable | string (e.g. "1+2")
│   ├── taxid               → nullable | integer
│   └── update_costprice    → boolean (true = update HPP manual)
└── payment{}           → required | object
    ├── paymenttype         → required | exists:paymenttype,id
    ├── refpayment          → nullable | string
    └── duedate             → required_if:purchasetype,2 | date
```

---

### 4.3 Controller (Thin)

**`app/Http/Controllers/Api/PurchaseController.php`**

| Method | HTTP | Endpoint | Deskripsi |
|---|---|---|---|
| `index` | GET | `/api/purchases` | List transaksi pembelian + filter |
| `store` | POST | `/api/purchases` | Buat transaksi pembelian baru |
| `show` | GET | `/api/purchases/{id}` | Detail transaksi pembelian |
| `getSupplierCreditInfo` | GET | `/api/purchases/supplier/{id}/credit` | Info limit & outstanding kredit supplier |

---

### 4.4 Route Tambahan

**`routes/api.php`** — ditambahkan:
```php
Route::prefix('purchases')->middleware('auth:sanctum')->group(function () {
    Route::get('/', [PurchaseController::class, 'index']);
    Route::post('/', [PurchaseController::class, 'store']);
    Route::get('/supplier/{supplierId}/credit', [PurchaseController::class, 'getSupplierCreditInfo']);
    Route::get('/{id}', [PurchaseController::class, 'show']);
});
```

---

## 5. Alur Eksekusi Lengkap (dalam satu DB Transaction)

```
POST /api/purchases
        │
        ▼
[1] Validasi input via CreatePurchaseRequest
        │
        ▼
[2] Ambil data supplier (termofpayment, creditlimit, payableacc)
        │
        ▼
[3] Jika purchasetype = CREDIT:
    └─ Hitung outstanding hutang ke supplier
    └─ Jika (outstanding + total) > creditlimit → BLOKIR, return 422
        │
        ▼
[4] Generate purchaseid:
    └─ UPDATE division SET purchaseidno = purchaseidno + 1
    └─ Format: prefix + lpad(purchaseidno, 6, '0')  → contoh: "I/PC-000128"
        │
        ▼
[5] Untuk setiap item di `items[]`:
    ├─ Hitung: grossamount = qty × price
    ├─ Hitung: valuedisc, purchasetax, netamount
    ├─ Jika update_costprice = true:
    │   ├─ UPDATE productmanagement SET costprice, netpurchase ...
    │   ├─ UPDATE product SET costprice, netpurchase, supplier ...
    │   └─ UPDATE inventory SET invvalue = new_price
    │          WHERE reference = purchaseid AND productid = ? AND transid <> purchaseid
    └─ INSERT inventory (invin = qty, invout = 0, invvalue = price, transtype = 1)
        │
        ▼
[6] INSERT purchase (header transaksi)
        │
        ▼
[7] INSERT purchasedetail (satu baris per item)
        │
        ▼
[8] Parse termofpayment → set duedate, earlydiscdays, earlydiscvalue
    INSERT purchasepayments:
    ├─ CASH     → duedate = purchasedate, accepted = 1
    ├─ COD      → duedate = purchasedate, accepted = 1
    └─ CREDIT   → duedate = purchasedate + duedays, accepted = 0
        │
        ▼
[9] Generate jurnal akuntansi:
    ├─ INCREMENT division.journalentryidno
    ├─ INSERT journal (jtid, jtdate, memo, division, approved = 1)
    └─ INSERT journaltrans × 2:
        ├─ Debit:  inventoryacc (nilai total pembelian)
        └─ Kredit: payableacc / kas (nilai total pembelian)
        │
        ▼
[10] COMMIT → Return response sukses
```

---

## 6. Standar Response API

Semua endpoint mengikuti format response yang konsisten:

**Success (201 Created)**:
```json
{
  "status": "success",
  "message": "Transaksi pembelian berhasil disimpan",
  "data": {
    "purchaseid": "I/PC-000128",
    "purchasedate": "2026-07-13",
    "supplierid": "ABE FASHION",
    "purchasetype": 2,
    "total_gross": 1802500,
    "total_disc": 6650,
    "total_net": 1795850,
    "items": [
      {
        "productid": "10060",
        "qty": 2,
        "price": 332500,
        "update_costprice": true,
        "netamount": 658350
      }
    ],
    "payment": {
      "duedate": "2026-08-12",
      "paymenttype": 3,
      "outstanding": 1795850
    }
  }
}
```

**Error — Credit Limit Exceeded (422)**:
```json
{
  "status": "error",
  "message": "Transaksi diblokir. Limit kredit pemasok terlampaui.",
  "data": {
    "supplierid": "ABE FASHION",
    "credit_limit": 5000000,
    "outstanding_debt": 4500000,
    "transaction_amount": 1795850,
    "total_if_approved": 6295850,
    "exceeded_by": 1295850
  }
}
```

---

## 7. Tabel Database yang Terlibat

| Tabel | Operasi | Keterangan |
|---|---|---|
| `division` | UPDATE | Increment `purchaseidno`, `journalentryidno` |
| `purchase` | INSERT | Header transaksi |
| `purchasedetail` | INSERT | Detail per produk |
| `purchasepayments` | INSERT | Info pembayaran & tempo |
| `inventory` | INSERT + UPDATE | Tambah stok masuk + recalc HPP lama |
| `product` | UPDATE (kondisional) | Update `costprice` jika user pilih manual |
| `productmanagement` | UPDATE (kondisional) | Update `costprice` per divisi |
| `journal` | INSERT | Header jurnal akuntansi |
| `journaltrans` | INSERT | Detail debit/kredit jurnal |
| `supplier` | SELECT | Baca `creditlimit`, `termofpayment`, `payableacc` |

---

## 8. Rencana Verifikasi

### Automated Tests
```bash
php artisan test --filter PurchaseTest
php artisan test --filter PurchaseServiceTest
```

### Skenario Test

| # | Skenario | Expected Result |
|---|---|---|
| 1 | Pembelian CASH, harga tidak berubah | Stok +, HPP tetap, jurnal tercatat |
| 2 | Pembelian CREDIT, update harga manual ON | Stok +, `costprice` di-update, HPP lama recalc, duedate sesuai term |
| 3 | Pembelian CREDIT, melebihi credit limit | **Transaksi DIBLOKIR**, response error + detail sisa limit |
| 4 | Pembelian CREDIT, update harga manual OFF | Stok +, `costprice` **tidak** berubah |
| 5 | Parsing `"2/10, n/30"` | `earlydiscdays=10`, `earlydiscvalue=2%`, `duedays=30` |
| 6 | Parsing `"COD"` | `purchasetype=0`, `duedays=0`, `accepted=1` |
| 7 | Jurnal akuntansi | Debit inventory = kredit payable, nilai sesuai total net |
| 8 | Rollback jika ada error di tengah proses | Semua tabel rollback, tidak ada data parsial |

---

> [!NOTE]
> Dokumen ini merupakan rencana teknis awal. Detail implementasi dapat berubah sesuai temuan di lapangan selama proses development.
