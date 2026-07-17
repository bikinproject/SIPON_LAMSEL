Benar. Karena gambar **MASTER REFERENCE sudah jadi**, sekarang lanjutkan di **obrolan Gem yang sama**. Jangan membuat konsep rumah baru lagi.

Apabila gambar itu dibuat dalam percakapan Gem tersebut, Anda bisa langsung membalas di bawah gambarnya. Gemini mendukung penyuntingan gambar yang dibuat di Gemini maupun gambar yang diunggah kembali. Namun, tetap unduh gambar ukuran penuh sebagai cadangan. ([Google Help][1])

## Langkah 1 — Simpan gambar master

Unduh gambar tersebut, lalu beri nama:

```text
MKH001_MASTER_FINAL_V01_APPROVED.png
```

Gambar master ini sekaligus menjadi:

```text
MKH001_STATE_09_LANDSCAPE_FINAL_V01_APPROVED.png
```

Tidak perlu membuat gambar State 09 lagi karena master Anda sudah menunjukkan rumah dalam keadaan selesai.

Jangan masukkan gambar ini ke bagian **Knowledge/Informasi Gem**. Bagian tersebut lebih cocok untuk aturan permanen Gem. Gambar master adalah aset khusus satu proyek, jadi gunakan sebagai lampiran dalam percakapan proyek. Gems memang menerima file Knowledge, tetapi file di sana digunakan sebagai referensi permanen Gem. ([Google Help][2])

## Langkah 2 — Daftarkan gambar sebagai master

Unggah kembali gambar tersebut ke obrolan Gem, atau balas langsung pada gambar yang telah dibuat. Kirim perintah ini:

```text
Gambar yang saya lampirkan sekarang resmi disetujui sebagai:

PROJECT CODE:
MKH001

MASTER REFERENCE:
MKH001_MASTER_FINAL_V01_APPROVED

CONSTRUCTION STATE:
MKH001_STATE_09_LANDSCAPE_FINAL_V01_APPROVED

Mulai sekarang, gambar ini adalah sumber identitas visual absolut proyek.

Jangan mendesain ulang bangunan.

Kunci elemen berikut berdasarkan gambar:
- bentuk dan proporsi massa bangunan;
- posisi balkon;
- posisi pintu dan seluruh jendela;
- bentuk atap;
- jumlah lantai;
- ukuran base platform;
- material dan warna;
- sudut kamera;
- framing vertikal 9:16;
- perspektif dan vanishing points;
- arah pencahayaan dan bayangan;
- posisi rumah di dalam frame.

Untuk saat ini jangan membuat gambar dan jangan membuat video.

Analisis gambar tersebut lalu keluarkan ARCHITECTURAL LOCK SHEET yang mencatat secara rinci semua elemen yang wajib dipertahankan pada State 00 sampai State 09.
```

Gem seharusnya membalas dengan deskripsi bentuk rumah. Periksa apakah ia membaca gambar dengan benar, terutama:

* balkon di kiri;
* pintu di kanan;
* jumlah dan posisi jendela;
* bentuk atap;
* warna material;
* sudut kamera.

Apabila deskripsinya salah, koreksi sebelum melanjutkan.

## Langkah 3 — Mulai reverse deconstruction dari State 08

Setelah Lock Sheet benar, jangan meminta seluruh state sekaligus. Buat **satu gambar per tahap**, dimulai dari State 08.

State 09 adalah rumah lengkap dengan lanskap. State 08 adalah rumah yang sama, tetapi sebelum taman dipasang.

Kirimkan:

```text
Sekarang buat hanya:

MKH001_STATE_08_WINDOWS_DOORS_FACADE_V01

Gunakan gambar MASTER REFERENCE yang saya lampirkan sebagai sumber edit langsung.

Lakukan reverse deconstruction dari State 09 menuju State 08.

Hapus hanya:
- rumput;
- tanaman tropis;
- pohon miniatur;
- stepping stones;
- lampu taman;
- seluruh elemen lanskap dekoratif.

Pertahankan secara identik:
- rumah;
- pondasi yang terlihat;
- base platform;
- semua dinding;
- balkon;
- atap;
- pintu;
- jendela;
- kaca;
- kusen;
- railing;
- panel kayu;
- material fasad;
- posisi kamera;
- framing 9:16;
- perspektif;
- pencahayaan;
- bayangan;
- ukuran dan posisi bangunan.

Area bekas lanskap harus menjadi permukaan base platform studio yang bersih dan polos.

Jangan mengubah, memindahkan, menambah, atau mendesain ulang bagian rumah apa pun.

Tidak ada manusia, kendaraan, alat, teks, logo, atau watermark.

Hasilkan satu gambar saja.
```

## Langkah 4 — Periksa hasil State 08

Bandingkan dengan gambar master. Yang boleh berubah hanya taman.

Tolak hasil apabila terjadi salah satu hal berikut:

* ukuran rumah berubah;
* balkon berpindah;
* jendela berubah jumlah;
* pintu berubah;
* atap berubah;
* framing menjadi lebih dekat;
* warna material bergeser;
* base platform berubah bentuk.

Apabila belum konsisten, jangan lanjut ke State 07. Minta revisi:

```text
Hasil belum disetujui.

Buat revisi:
MKH001_STATE_08_WINDOWS_DOORS_FACADE_V02

Masalah yang harus diperbaiki:
[tuliskan masalahnya, misalnya posisi balkon berubah atau ukuran jendela berbeda]

Gunakan kembali MASTER REFERENCE sebagai dasar edit.

Ubah hanya masalah yang saya sebutkan. Pertahankan seluruh elemen lainnya.
```

Setelah bagus, simpan:

```text
MKH001_STATE_08_WINDOWS_DOORS_FACADE_V02_APPROVED.png
```

## Langkah 5 — Buat State berikutnya secara mundur

Setelah State 08 disetujui, gunakan **State 08**, bukan gambar master, untuk membuat State 07.

Urutannya:

```text
STATE 09 → hapus lanskap → STATE 08
STATE 08 → hapus kaca, pintu, kusen, railing → STATE 07
STATE 07 → hapus atap → STATE 06
STATE 06 → hapus dinding dan struktur lantai dua → STATE 05
STATE 05 → hapus pelat lantai dua → STATE 04
STATE 04 → hapus panel dinding lantai dasar → STATE 03
STATE 03 → hapus kolom dan balok → STATE 02
STATE 02 → hapus pelat lantai dasar → STATE 01
STATE 01 → hapus pondasi → STATE 00
```

Catatan penting: pada State 07, dinding harus tetap memiliki bukaan pintu dan jendela. Yang dilepas hanya kaca, kusen, daun pintu, serta railing—bukan menutup lubang bukaan.

## Perintah singkat untuk State 07

Setelah State 08 disetujui, unggah State 08 dan kirim:

```text
Gambar yang saya lampirkan adalah:

CURRENT SOURCE:
MKH001_STATE_08_WINDOWS_DOORS_FACADE_APPROVED

Buat:
MKH001_STATE_07_FLAT_ROOF_V01

Lakukan reverse deconstruction.

Hapus hanya:
- panel kaca;
- seluruh kusen aluminium;
- daun pintu utama;
- railing balkon;
- elemen finishing fasad tambahan yang dipasang pada State 08.

Pertahankan bukaan pintu dan jendela pada dinding sebagai lubang arsitektural yang rapi.

Pertahankan semua geometri, dinding, panel kayu struktural, balkon, atap, base platform, kamera, framing, pencahayaan, dan bayangan.

Jangan menghasilkan gambar rumah baru dari teks kosong. Edit gambar sumber yang dilampirkan.
```

## Setelah semua gambar state selesai

Baru buat videonya **maju**, bukan mundur:

```text
STATE 00 → STATE 01
STATE 01 → STATE 02
STATE 02 → STATE 03
...
STATE 08 → STATE 09
```

Untuk setiap klip, gunakan gambar state awal sebagai first frame dan state berikutnya sebagai last frame. Veo 3.1 mendukung pengarahan dengan frame awal dan akhir serta gambar referensi tambahan. ([Google AI for Developers][3])

Jadi langkah Anda sekarang adalah:

**unduh master → beri nama → unggah/balas di Gem yang sama → tetapkan sebagai State 09 → buat State 08 dengan menghapus lanskap saja.**

[1]: https://support.google.com/gemini/answer/14286560?co=GENIE.Platform%3DAndroid&hl=en&utm_source=chatgpt.com "Generate & edit images with Gemini Apps - Android"
[2]: https://support.google.com/gemini/answer/15235603?hl=en&utm_source=chatgpt.com "Tips for creating custom Gems - Gemini Apps Help"
[3]: https://ai.google.dev/gemini-api/docs/veo?utm_source=chatgpt.com "Generate videos with Veo 3.1 in Gemini API"
