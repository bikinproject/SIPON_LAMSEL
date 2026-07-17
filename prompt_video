Ada. Namun buat **satu video untuk satu transisi**, bukan satu prompt untuk State 00 sampai State 09 sekaligus.

Untuk kontrol paling presisi, gunakan **Google Flow → Video → Frames**. Masukkan State awal ke **Add start frame** dan State berikutnya ke **Add end frame**, kemudian tempel prompt transisinya. Flow memang menyediakan kontrol start frame dan end frame secara eksplisit. Dukungan durasi bergantung pada model yang dipilih; untuk first-and-last-frame, 8 detik adalah pilihan yang sesuai untuk workflow ini. ([Google Help][1])

Gemini Apps juga dapat menerima hingga lima gambar referensi dan melakukan pengeditan video dalam percakapan. Namun, untuk pekerjaan yang membutuhkan State A sebagai frame awal dan State B sebagai frame akhir secara jelas, Flow secara praktis lebih mudah dikendalikan. ([Google Help][2])

## Cara memasukkan setiap klip di Flow

Untuk contoh klip pertama:

* Start frame: `MKH001_STATE_00_EMPTY_BASE_V01_APPROVED`
* End frame: `MKH001_STATE_01_FOUNDATION_V01_APPROVED`
* Rasio: `9:16`
* Durasi: `8 seconds`
* Camera motion: tidak ada
* Prompt: gunakan prompt `00_TO_01` di bawah.

---

## CLIP 00 → 01 — Pemasangan Pondasi

```text
Use the attached START FRAME as the exact first frame:

MKH001_STATE_00_EMPTY_BASE_V01_APPROVED

Use the attached END FRAME as the exact final frame:

MKH001_STATE_01_FOUNDATION_V01_APPROVED

Create an 8-second vertical 9:16 photorealistic miniature architectural
model-kit assembly video.

[0.0–1.0s]
Hold briefly on the completely empty light-grey studio base platform.

[1.0–2.0s]
Thin technical construction grid lines draw themselves precisely onto the
platform surface, matching the end frame exactly.

[2.0–6.5s]
Individual foundation footings and foundation beams enter from directly above
in a clean exploded-view arrangement. Every component remains rigid, moves
along a straight controlled path, aligns precisely with the technical grid,
and locks into its correct position with subtle mechanical snap-fit movement.

[6.5–7.2s]
The final foundation beam locks into place. All components stop moving.

[7.2–8.0s]
Hold completely still on the exact approved end frame.

The transformation must end with the foundation geometry, footprint, grid
lines, platform, shadows, and composition matching the supplied END FRAME.

Locked static three-quarter front-left camera, slightly elevated perspective,
fixed framing, fixed focal length, no zoom, no orbit, no camera shake.

No humans, no workers, no hands, no robots, no vehicles, no tools, no cranes,
no text, no logos, no cuts, no fade, no morphing, no deformation, no geometry
drift, no spontaneous future components, no slab, no columns, no walls, no roof.

Audio: subtle concrete placement sounds, precision mechanical clicks, quiet
studio ambience, no speech and no music.
```

Simpan videonya sebagai:

```text
MKH001_CLIP_00_TO_01_FOUNDATION_V01.mp4
```

---

## CLIP 01 → 02 — Pelat Lantai Dasar

```text
Use the attached START FRAME as the exact first frame:

MKH001_STATE_01_FOUNDATION_V01_APPROVED

Use the attached END FRAME as the exact final frame:

MKH001_STATE_02_GROUND_FLOOR_SLAB_V01_APPROVED

Create an 8-second vertical 9:16 photorealistic miniature architectural
model-kit assembly video.

[0.0–1.0s]
Hold on the completed foundation. The foundation and platform remain perfectly
stationary.

[1.0–6.3s]
Precisely shaped reinforced-concrete ground-floor slab sections descend
vertically from above in an organized exploded-view arrangement.

The slab components maintain rigid geometry, align perfectly over the existing
foundation, and assemble section by section without intersecting one another.

[6.3–7.2s]
The final slab section lowers into position and locks with a restrained,
precision snap-fit movement.

[7.2–8.0s]
Hold completely still on the exact approved end frame.

Animate only the installation of the ground-floor slab. The existing
foundation must not move, resize, disappear, or change material.

Locked camera, fixed perspective, fixed framing, fixed platform, identical
lighting direction and shadows.

No humans, hands, workers, tools, vehicles, text, cuts, fades, camera movement,
morphing, deformation, duplicated slab sections, columns, walls, upper floors,
roof, windows, facade, or landscaping.

Audio: subtle concrete contact sounds and precise mechanical locking clicks.
No dialogue and no music.
```

Nama file:

```text
MKH001_CLIP_01_TO_02_GROUND_SLAB_V01.mp4
```

---

## CLIP 02 → 03 — Kolom dan Balok

```text
Use the attached START FRAME as the exact first frame:

MKH001_STATE_02_GROUND_FLOOR_SLAB_V01_APPROVED

Use the attached END FRAME as the exact final frame:

MKH001_STATE_03_COLUMNS_BEAMS_V01_APPROVED

Create an 8-second vertical 9:16 miniature architectural model-kit assembly
video.

[0.0–1.0s]
Hold on the completed ground-floor slab.

[1.0–4.2s]
Structural columns rise vertically from their exact connection points on the
slab, one coordinated group at a time. They remain straight, rigid, and
dimensionally stable.

[4.2–6.7s]
Horizontal structural beams enter from the left and right edges of the frame,
align with the column tops, and lock precisely into place.

[6.7–7.2s]
All structural connections complete with subtle mechanical snap-fit movements.

[7.2–8.0s]
Hold completely still on the exact approved end frame.

Animate only the approved structural columns and beams. Preserve the slab,
foundation, footprint, platform, camera, framing, perspective, materials,
lighting, and shadows.

No wall panels, upper-floor slab, roof, doors, windows, facade, landscaping,
humans, workers, hands, tools, cranes, vehicles, camera movement, cuts, fades,
morphing, bending, material changes, geometry drift, duplicated members, or
floating components at the end.

Audio: restrained structural locking clicks and quiet studio ambience.
```

Nama file:

```text
MKH001_CLIP_02_TO_03_STRUCTURE_V01.mp4
```

---

## CLIP 03 → 04 — Dinding Lantai Dasar

```text
Use the attached START FRAME as the exact first frame:

MKH001_STATE_03_COLUMNS_BEAMS_V01_APPROVED

Use the attached END FRAME as the exact final frame:

MKH001_STATE_04_GROUND_FLOOR_WALLS_V01_APPROVED

Create an 8-second vertical 9:16 miniature architectural model-kit assembly
video.

[0.0–1.0s]
Hold on the exposed ground-floor structural frame.

[1.0–6.5s]
Rigid wall panels enter from outside the frame in a controlled exploded-view
sequence. White concrete panels, approved wood wall sections, and grey stone
infill panels slide precisely between the existing columns and beneath the
structural beams.

Every approved door and window opening must remain open and retain its exact
size, position, and proportions.

[6.5–7.2s]
The final wall panel locks into its structural bay. Everything stops moving.

[7.2–8.0s]
Hold completely still on the exact approved end frame.

Animate only the wall-panel installation. Do not move or alter the columns,
beams, slab, foundation, or platform.

No glass, window frames, door leaf, upper floor, balcony, roof, facade
accessories, landscaping, humans, hands, tools, vehicles, camera movement,
cuts, fades, morphing, shrinking openings, closing openings, deformation, or
geometry drift.

Audio: subtle panel sliding and soft snap-fit locking sounds.
```

Nama file:

```text
MKH001_CLIP_03_TO_04_GROUND_WALLS_V01.mp4
```

---

## CLIP 04 → 05 — Pelat Lantai Dua dan Balkon

```text
Use the attached START FRAME as the exact first frame:

MKH001_STATE_04_GROUND_FLOOR_WALLS_V01_APPROVED

Use the attached END FRAME as the exact final frame:

MKH001_STATE_05_SECOND_FLOOR_SLAB_V01_APPROVED

Create an 8-second vertical 9:16 miniature architectural model-kit assembly
video.

[0.0–1.0s]
Hold on the completed open-top ground floor.

[1.0–5.8s]
Multiple rigid second-floor slab sections descend vertically from above,
remaining perfectly level. They align precisely with the ground-floor columns,
walls, and structural support points.

[5.8–6.8s]
The left-side cantilevered balcony slab slides horizontally into its approved
position and locks firmly into the second-floor slab.

[6.8–7.2s]
All slab joints settle into position with restrained precision clicks.

[7.2–8.0s]
Hold completely still on the exact approved end frame.

Animate only the second-floor slab and balcony slab. Preserve all ground-floor
geometry and openings exactly.

No upper-floor columns, upper walls, railings, windows, doors, roof, facade
finishing, landscaping, humans, hands, machinery, camera movement, cuts,
fades, morphing, bending slabs, deformation, geometry drift, or floating parts.

Audio: subtle concrete placement and mechanical locking sounds.
```

Nama file:

```text
MKH001_CLIP_04_TO_05_SECOND_FLOOR_V01.mp4
```

---

## CLIP 05 → 06 — Struktur dan Dinding Lantai Dua

```text
Use the attached START FRAME as the exact first frame:

MKH001_STATE_05_SECOND_FLOOR_SLAB_V01_APPROVED

Use the attached END FRAME as the exact final frame:

MKH001_STATE_06_UPPER_WALLS_STRUCTURE_V01_APPROVED

Create an 8-second vertical 9:16 miniature architectural model-kit assembly
video.

[0.0–1.0s]
Hold on the exposed second-floor slab and balcony slab.

[1.0–3.7s]
Second-floor structural columns rise vertically from their exact approved
connection points.

[3.7–6.5s]
Upper-floor wall panels and approved warm wood wall sections enter in a clean
exploded-view sequence and lock between the structural members.

All upper-floor window and door openings remain clean, empty, correctly sized,
and exactly positioned.

[6.5–7.2s]
The final upper wall panel locks into place. All movement stops.

[7.2–8.0s]
Hold completely still on the exact approved end frame.

Animate only the upper-floor structure and wall panels. Preserve the balcony
slab, lower floor, platform, camera, perspective, lighting, and shadows.

No roof, glass, frames, doors, railings, landscaping, humans, workers, hands,
tools, vehicles, camera movement, cuts, fades, morphing, resized openings,
deformation, material drift, or geometry drift.

Audio: light structural clicks and subtle panel locking sounds.
```

Nama file:

```text
MKH001_CLIP_05_TO_06_UPPER_STRUCTURE_V01.mp4
```

---

## CLIP 06 → 07 — Pemasangan Atap

```text
Use the attached START FRAME as the exact first frame:

MKH001_STATE_06_UPPER_WALLS_STRUCTURE_V01_APPROVED

Use the attached END FRAME as the exact final frame:

MKH001_STATE_07_BUILDING_SHELL_V01_APPROVED

Create an 8-second vertical 9:16 miniature architectural model-kit assembly
video.

[0.0–1.2s]
Hold on the completed open-top second-floor structure.

[1.2–6.5s]
Rigid tiered flat-roof sections descend vertically from above in a precise
layered sequence. Each roof section remains level, maintains sharp geometric
edges, and aligns exactly with the approved upper-floor walls and columns.

Roof overhangs, fascia sections, and edge components attach in the correct
order without intersecting the existing structure.

[6.5–7.2s]
The final roof component locks into position. All parts stop moving.

[7.2–8.0s]
Hold completely still on the exact approved end frame.

Animate only the approved roof components. Preserve every existing wall,
opening, balcony slab, material, platform, camera, framing, lighting, and
shadow.

No windows, glass, doors, frames, railings, facade accessories, landscaping,
humans, tools, cranes, vehicles, camera movement, cuts, fades, morphing,
warped roof planes, deformation, or geometry drift.

Audio: restrained roof placement sounds and precision locking clicks.
```

Nama file:

```text
MKH001_CLIP_06_TO_07_ROOF_V01.mp4
```

---

## CLIP 07 → 08 — Kaca, Kusen, Pintu, dan Railing

```text
Use the attached START FRAME as the exact first frame:

MKH001_STATE_07_BUILDING_SHELL_V01_APPROVED

Use the attached END FRAME as the exact final frame:

MKH001_STATE_08_NO_LANDSCAPE_V01_APPROVED

Create an 8-second vertical 9:16 miniature architectural model-kit assembly
video.

[0.0–1.0s]
Hold on the completed building shell with clean empty architectural openings.

[1.0–3.8s]
Matte-black aluminum frames enter directly toward their matching openings and
lock precisely into place.

[3.8–5.8s]
Clear architectural glass panels slide carefully into the installed frames,
remaining rigid and undistorted.

[5.8–6.7s]
The main entrance door and approved facade accessories attach to their exact
locations.

[6.7–7.2s]
Minimalist balcony railings rise vertically from the balcony slab and lock
into place.

[7.2–8.0s]
Hold completely still on the exact approved end frame.

Animate only the approved frames, glass, entrance door, railing, and facade
finishing. Do not alter the building shell.

No landscaping, grass, plants, trees, humans, workers, hands, tools, vehicles,
camera movement, cuts, fades, morphing, distorted glass, new openings,
changed openings, duplicated frames, material drift, or geometry drift.

Audio: soft glass placement, subtle metal clicks, and quiet studio ambience.
```

Nama file:

```text
MKH001_CLIP_07_TO_08_FACADE_V01.mp4
```

---

## CLIP 08 → 09 — Lanskap dan Final Reveal

Start frame:

```text
MKH001_STATE_08_NO_LANDSCAPE_V01_APPROVED
```

End frame dapat menggunakan:

```text
MKH001_MASTER_FINAL_V01_APPROVED
```

atau file yang sama dengan nama:

```text
MKH001_STATE_09_LANDSCAPE_FINAL_V01_APPROVED
```

Prompt:

```text
Use the attached START FRAME as the exact first frame:

MKH001_STATE_08_NO_LANDSCAPE_V01_APPROVED

Use the attached END FRAME as the exact final frame:

MKH001_STATE_09_LANDSCAPE_FINAL_V01_APPROVED

Create an 8-second vertical 9:16 miniature architectural model-kit assembly
video.

[0.0–1.0s]
Hold on the completed house standing on the clean bare studio platform.

[1.0–3.5s]
Precisely shaped miniature grass sections descend vertically and fit cleanly
into their approved locations around the house.

[3.5–5.5s]
Stepping stones and small garden components enter in an orderly sequence and
settle exactly into the positions shown in the end frame.

[5.5–6.8s]
Miniature tropical plants and trees rise mechanically from their approved
mounting points. Garden lights attach with restrained snap-fit movements.

[6.8–7.2s]
The final landscape component locks into place. Everything becomes motionless.

[7.2–8.0s]
Hold on the fully completed architectural model, matching the exact approved
end frame.

Animate only landscaping elements. The house must remain completely unchanged
throughout the entire clip.

Locked camera, fixed framing, fixed perspective, identical building position,
materials, lighting direction, and shadows.

No humans, workers, hands, gardening tools, vehicles, camera movement, cuts,
fades, morphing plants, organic growth, magical appearance, changed
architecture, changed windows, changed roof, changed balcony, geometry drift,
or additional decorative objects.

Audio: subtle miniature placement sounds, gentle mechanical clicks, and quiet
premium studio ambience. No speech.
```

Nama file:

```text
MKH001_CLIP_08_TO_09_FINAL_REVEAL_V01.mp4
```

## Ketika hasil video berubah bentuk

Jangan menulis ulang seluruh prompt. Gunakan prompt koreksi ini dengan start dan end frame yang sama:

```text
Regenerate this transition using the same supplied start frame and end frame.

The previous result is rejected because the architectural geometry changed.

The only permitted visual change is:

[WRITE THE COMPONENT BEING INSTALLED]

Do not reinterpret or redesign the building.

Preserve the exact building footprint, dimensions, balcony position, roof
shape, openings, materials, camera, perspective, framing, lighting, shadows,
platform, and composition shown in the supplied frames.

The final second must match the supplied end frame as closely as possible.

No camera movement, no morphing, no geometry drift, no material drift, no
additional components, and no components from later construction states.
```

Buat dan setujui satu klip sebelum melanjutkan ke klip berikutnya. Setelah sembilan klip selesai, gabungkan secara berurutan di CapCut atau editor lain, lalu potong bagian hold yang terlalu panjang agar hasil akhir terasa lebih cepat.

[1]: https://support.google.com/flow/answer/16353334?co=GENIE.Platform%3DDesktop&hl=en&utm_source=chatgpt.com "Create videos in Google Flow - Computer"
[2]: https://support.google.com/gemini/answer/16126339?co=GENIE.Platform%3DAndroid&hl=en&utm_source=chatgpt.com "Generate videos with Gemini Apps - Android"
