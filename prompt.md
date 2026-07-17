Iya. Setelah `STATE_08` disetujui, buat state berikutnya **secara mundur satu per satu**. Jangan meminta Gemini membuat semuanya sekaligus.

Setiap gambar yang sudah benar harus diunduh dan diberi nama `APPROVED` secara manual. Gemini biasanya tidak benar-benar menentukan nama file meskipun nama dicantumkan dalam prompt.

Urutan reverse deconstruction:

```text
STATE 08 → STATE 07
STATE 07 → STATE 06
STATE 06 → STATE 05
STATE 05 → STATE 04
STATE 04 → STATE 03
STATE 03 → STATE 02
STATE 02 → STATE 01
STATE 01 → STATE 00
```

## STATE 07 — Building Shell

Unggah:

```text
MKH001_STATE_08_NO_LANDSCAPE_V01_APPROVED
```

Gunakan prompt:

```text
The attached image is the approved source:

MKH001_STATE_08_NO_LANDSCAPE_V01_APPROVED

Create one edited still image:

MKH001_STATE_07_BUILDING_SHELL_V01

REVERSE DECONSTRUCTION TASK:

Remove only:
- all glass panels;
- all black aluminum window frames;
- the main entrance door leaf and its frame;
- balcony railings;
- decorative facade accessories;
- non-structural exterior trim installed during the facade-finishing stage.

Keep all architectural door and window openings visible as clean, empty openings.

PRESERVE EXACTLY:
- flat roof geometry;
- roof overhangs;
- upper-floor walls;
- ground-floor walls;
- structural columns and beams;
- balcony slab;
- wall openings;
- white concrete surfaces;
- warm wood wall sections that are part of the permanent building shell;
- grey stone structural surfaces;
- building proportions;
- base platform;
- camera position;
- three-quarter front-left viewing angle;
- vertical 9:16 framing;
- perspective and vanishing points;
- lighting direction;
- shadows;
- building position and scale.

Do not close, resize, move, add, or redesign any architectural opening.

Do not generate a new house from text. Edit the attached approved source image directly.

No humans, no workers, no hands, no tools, no vehicles, no text, no logos, no watermark, no camera movement, no geometry drift, no material changes, no background changes, no deformation.

Output exactly one still image, not a video.
```

Setelah benar, simpan:

```text
MKH001_STATE_07_BUILDING_SHELL_V01_APPROVED.png
```

---

## STATE 06 — Upper Floor Walls and Structure

Unggah State 07 yang telah disetujui.

```text
The attached image is the approved source:

MKH001_STATE_07_BUILDING_SHELL_V01_APPROVED

Create one edited still image:

MKH001_STATE_06_UPPER_WALLS_STRUCTURE_V01

REVERSE DECONSTRUCTION TASK:

Remove only:
- the complete flat roof slab;
- tiered roof sections;
- roof overhang components;
- roof fascia and roof-edge finishing;
- roof caps or roof-covering components.

The roof must be fully absent, revealing the open top of the second-floor structure.

PRESERVE EXACTLY:
- all second-floor walls;
- second-floor structural columns and beams;
- all existing door and window openings;
- balcony slab;
- ground-floor walls;
- ground-floor structure;
- white concrete;
- warm wood wall sections;
- grey stone surfaces;
- base platform;
- building geometry and proportions;
- camera position;
- vertical 9:16 framing;
- perspective;
- lighting;
- shadows;
- building placement and scale.

Do not remove upper-floor walls, columns, balcony slab, or lower-floor elements.

Do not add temporary supports, construction tools, people, cranes, or new components.

Do not generate a new building. Edit only the attached approved source image.

No humans, no workers, no hands, no tools, no vehicles, no text, no logos, no watermark, no camera movement, no geometry drift, no new openings, no resized openings, no material changes, no background changes, no deformation.

Output exactly one still image, not a video.
```

Simpan sebagai:

```text
MKH001_STATE_06_UPPER_WALLS_STRUCTURE_V01_APPROVED.png
```

---

## STATE 05 — Second-Floor Slab and Balcony Slab

Unggah State 06 yang disetujui.

```text
The attached image is the approved source:

MKH001_STATE_06_UPPER_WALLS_STRUCTURE_V01_APPROVED

Create one edited still image:

MKH001_STATE_05_SECOND_FLOOR_SLAB_V01

REVERSE DECONSTRUCTION TASK:

Remove only:
- all second-floor wall panels;
- all second-floor structural columns;
- all second-floor structural beams above the floor slab;
- all warm wood cladding attached to the second-floor walls;
- all upper-floor architectural openings together with the removed walls.

Leave the second-floor horizontal slab fully installed.

Leave the left-side balcony cantilever slab fully installed.

The result must show the completed ground floor supporting an exposed second-floor slab and balcony slab, with no upper-floor walls and no roof.

PRESERVE EXACTLY:
- second-floor slab dimensions;
- balcony cantilever slab;
- ground-floor walls;
- ground-floor door and window openings;
- ground-floor structural elements;
- white concrete surfaces;
- grey stone surfaces;
- base platform;
- overall building footprint;
- camera position;
- framing;
- perspective;
- lighting;
- shadows;
- building placement and scale.

Do not remove or deform the second-floor slab.

Do not add railings, windows, doors, roof parts, landscaping, tools, or temporary construction elements.

Do not regenerate the architecture. Edit the attached approved source directly.

No humans, no workers, no hands, no vehicles, no text, no logos, no watermark, no camera movement, no geometry drift, no changed proportions, no changed materials, no background changes, no deformation.

Output exactly one still image, not a video.
```

Simpan:

```text
MKH001_STATE_05_SECOND_FLOOR_SLAB_V01_APPROVED.png
```

---

## STATE 04 — Ground-Floor Walls

Unggah State 05 yang disetujui.

```text
The attached image is the approved source:

MKH001_STATE_05_SECOND_FLOOR_SLAB_V01_APPROVED

Create one edited still image:

MKH001_STATE_04_GROUND_FLOOR_WALLS_V01

REVERSE DECONSTRUCTION TASK:

Remove only:
- the complete second-floor horizontal slab;
- the left-side balcony cantilever slab;
- all supporting components that belong exclusively to the second-floor slab installation stage.

The result must show the completed ground-floor walls and ground-floor structural system with an open top.

PRESERVE EXACTLY:
- all ground-floor walls;
- all ground-floor structural columns and beams;
- the main entrance opening on the right;
- the large window openings on the left;
- all other approved ground-floor openings;
- white concrete wall surfaces;
- warm wood sections that belong to the ground-floor walls;
- grey stone structural surfaces;
- ground-floor slab;
- foundation below it;
- building footprint;
- base platform;
- camera position;
- vertical 9:16 framing;
- perspective;
- lighting;
- shadows;
- building placement and scale.

Do not close, move, resize, or redesign any ground-floor opening.

Do not add a roof, upper walls, balcony, windows, doors, railings, or landscaping.

Do not regenerate the house. Edit only the attached approved source.

No humans, no workers, no hands, no tools, no vehicles, no text, no logos, no watermark, no camera movement, no geometry drift, no changed materials, no background changes, no deformation.

Output exactly one still image, not a video.
```

Simpan:

```text
MKH001_STATE_04_GROUND_FLOOR_WALLS_V01_APPROVED.png
```

---

## STATE 03 — Ground-Floor Columns and Beams

Unggah State 04 yang disetujui.

```text
The attached image is the approved source:

MKH001_STATE_04_GROUND_FLOOR_WALLS_V01_APPROVED

Create one edited still image:

MKH001_STATE_03_COLUMNS_BEAMS_V01

REVERSE DECONSTRUCTION TASK:

Remove only:
- all non-structural ground-floor wall panels;
- white concrete wall infill panels;
- warm wood wall panels;
- grey stone facade infill;
- all wall surfaces between the structural columns.

Expose the complete ground-floor structural frame.

The result must show:
- the approved ground-floor slab;
- structural columns;
- structural beams;
- open spaces where the walls previously existed.

PRESERVE EXACTLY:
- every structural column;
- every structural beam;
- their exact positions, thicknesses, heights, and spacing;
- ground-floor slab;
- foundation geometry;
- building footprint;
- base platform;
- camera position;
- vertical 9:16 framing;
- perspective;
- lighting;
- shadows;
- building placement and scale.

Do not remove columns or beams.

Do not add walls, upper floors, roof components, windows, doors, facade elements, landscaping, tools, or temporary supports.

Do not redesign the structural frame or invent new structural members.

Edit the attached approved source image directly.

No humans, no workers, no hands, no tools, no vehicles, no text, no logos, no watermark, no camera movement, no geometry drift, no changed column positions, no changed beam positions, no deformation, no background changes.

Output exactly one still image, not a video.
```

Simpan:

```text
MKH001_STATE_03_COLUMNS_BEAMS_V01_APPROVED.png
```

---

## STATE 02 — Ground-Floor Slab

Unggah State 03 yang disetujui.

```text
The attached image is the approved source:

MKH001_STATE_03_COLUMNS_BEAMS_V01_APPROVED

Create one edited still image:

MKH001_STATE_02_GROUND_FLOOR_SLAB_V01

REVERSE DECONSTRUCTION TASK:

Remove only:
- all vertical structural columns;
- all horizontal structural beams above the ground-floor slab;
- all remaining above-slab structural frame components.

Leave the complete ground-floor slab installed over the foundation.

The result must show a clean horizontal ground-floor slab with no walls, no columns, no beams, and no upper structure.

PRESERVE EXACTLY:
- ground-floor slab shape;
- ground-floor slab thickness;
- slab edges;
- building footprint;
- visible foundation elements beneath the slab;
- base platform;
- camera position;
- vertical 9:16 framing;
- perspective;
- lighting;
- shadows;
- slab position and scale.

Do not remove, resize, deform, split, or redesign the ground-floor slab.

Do not add markings, structures, walls, components, tools, machinery, or people.

Edit only the attached approved source image.

No humans, no workers, no hands, no tools, no vehicles, no text, no logos, no watermark, no camera movement, no geometry drift, no changed slab dimensions, no deformation, no background changes.

Output exactly one still image, not a video.
```

Simpan:

```text
MKH001_STATE_02_GROUND_FLOOR_SLAB_V01_APPROVED.png
```

---

## STATE 01 — Foundation

Unggah State 02 yang disetujui.

```text
The attached image is the approved source:

MKH001_STATE_02_GROUND_FLOOR_SLAB_V01_APPROVED

Create one edited still image:

MKH001_STATE_01_FOUNDATION_V01

REVERSE DECONSTRUCTION TASK:

Remove only:
- the complete ground-floor slab;
- all slab surface finishes;
- all horizontal floor surfaces installed above the foundation.

Reveal the complete foundation system below it.

The result must clearly show:
- foundation footings;
- foundation beams;
- the exact building footprint;
- thin technical construction grid lines on the studio base platform.

PRESERVE EXACTLY:
- foundation geometry;
- foundation positions;
- foundation proportions;
- building footprint;
- base-platform dimensions;
- camera position;
- vertical 9:16 framing;
- perspective;
- lighting direction;
- shadows;
- foundation placement and scale.

The technical grid lines must be subtle, precise, thin, and limited to the building footprint area.

Do not flatten or simplify the foundation into a single slab.

Do not add columns, walls, floor slabs, roof elements, facade components, landscaping, people, tools, or construction equipment.

Do not redesign the foundation. Edit the attached approved source directly.

No humans, no workers, no hands, no vehicles, no text labels, no measurements, no numbers, no logos, no watermark, no camera movement, no geometry drift, no deformation, no background changes.

Output exactly one still image, not a video.
```

Simpan:

```text
MKH001_STATE_01_FOUNDATION_V01_APPROVED.png
```

---

## STATE 00 — Empty Base Platform

Unggah State 01 yang disetujui.

```text
The attached image is the approved source:

MKH001_STATE_01_FOUNDATION_V01_APPROVED

Create one edited still image:

MKH001_STATE_00_EMPTY_BASE_V01

REVERSE DECONSTRUCTION TASK:

Remove only:
- all foundation footings;
- all foundation beams;
- all foundation components;
- all technical grid lines;
- all construction markings.

Leave only the original pristine light-grey studio base platform.

The result must show:
- an entirely empty base platform;
- no building components;
- no foundation;
- no slab;
- no columns;
- no walls;
- no roof;
- no facade;
- no landscaping.

PRESERVE EXACTLY:
- base-platform shape;
- base-platform dimensions;
- base-platform position;
- camera position;
- static three-quarter front-left viewing angle;
- slightly elevated perspective;
- vertical 9:16 framing;
- background;
- lighting direction;
- shadows;
- composition.

Do not remove, resize, crop, rotate, or redesign the base platform itself.

Do not add text, markings, objects, people, tools, vehicles, construction materials, vegetation, or decorative elements.

Edit only the attached approved source image.

No humans, no workers, no hands, no tools, no vehicles, no text, no logos, no watermark, no camera movement, no perspective change, no platform deformation, no background change.

Output exactly one still image, not a video.
```

Simpan:

```text
MKH001_STATE_00_EMPTY_BASE_V01_APPROVED.png
```

## Aturan pengerjaan

Setiap kali selesai membuat satu state:

1. Bandingkan dengan gambar sebelumnya.
2. Pastikan hanya komponen yang diminta yang hilang.
3. Tolak hasil apabila kamera, ukuran platform, perspektif, atau posisi bangunan berubah.
4. Unduh gambar yang benar.
5. Tambahkan `APPROVED` pada nama file.
6. Gunakan gambar approved tersebut sebagai sumber untuk state berikutnya.

Setelah seluruh gambar `STATE_00` sampai `STATE_09` selesai, pembuatan video dilakukan dengan urutan maju:

```text
STATE 00 → STATE 01
STATE 01 → STATE 02
STATE 02 → STATE 03
STATE 03 → STATE 04
STATE 04 → STATE 05
STATE 05 → STATE 06
STATE 06 → STATE 07
STATE 07 → STATE 08
STATE 08 → STATE 09
```
