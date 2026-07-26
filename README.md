# Casa Nira · Villa C3 — Upgraded Inventory

A single self-contained web page (`index.html`) showing the FF&E upgrade inventory and
custom-branding catalog for **Villa C3 · The Sanctuary** (3BR, 160 sqm).
Built on the shared Casa Nira inventory template.

## Baseline verification
The retained/upgraded rows were checked against Annex I ("Spesifikasi Villa dan Daftar
Perabot") of **`Unit C3 | Casa Nira - Draft Furnishing Agreement.pdf`**
(CN-C3-FURN-001, client PT Alchemy Estate Group).

- Annex I lists **80 items / 178 total units**
- **77 / 77 distinct item names matched**, aggregate quantity **178 = 178**
- 0 unresolved discrepancies

C3's annex is a **flat list with no category headers and no baseline-brand column**, unlike
C1's. Items were grouped into the standard five categories by position (1–24 electronics,
25–37 fixed, 38–59 loose, 60–80 amenities).

### C3-specific differences vs Villa C1

Removed — not in C3's annex:

| Item | C1 |
|---|---|
| Indoor Dining Chair | Dining ×4 |
| TV Credenza | Living Room ×1 |
| Standing Lamp | Living Room, Master Bedroom ×2 |
| Surf Rack | Outdoor Terrace ×1 |
| Sunbed Portable Table | Outdoor Terrace ×1 |
| Scrub Daddy | Kitchen ×4 |

Added — C3 only:

| Item | C3 |
|---|---|
| Indoor Dining Table | Dining ×1 |
| Bar Stool | Kitchen ×4 |
| Hanging Lamp (2nd row) | Living Room, Master Bedroom ×2 |

Changed:

| Item | C1 | C3 |
|---|---|---|
| Ceiling Speaker & Amplifier | ×4 | **×1** |
| Iron | All Bedrooms | Master Bedroom |
| TV Stand | All Bedrooms | Master Bedroom |
| Outdoor Dining Chair | ×3 | ×4 |
| Lazy Chair | LR + Master ×3 | Master Bedroom ×1 |
| Trash Can | ×6 | ×8 |

### Open items to confirm with the team
- **Baseline brands are not documented in C3's agreement** (no `Ex:` column). The
  `prevBrand` values shown are carried from the shared Casa Nira baseline
  (Onassis, Samsung, Gree, LG, Electrolux, Modena, Nespresso, TP-Link, Ecolux, Panasonic,
  Ariston, Ezviz, Philips, Azko, Turu, Indolinen, Terry Palmer, etc.) and should be
  confirmed before this goes to the owner.
- **Ceiling Speaker & Amplifier ×1** is unusual (C1/C2 both have ×4) — worth double-checking
  whether the annex means 1 *set* rather than 1 unit.
- Annex I lists the bathtub and bathroom mirrors under *Master Bedroom* / *All Bedrooms*;
  the page uses *Master Bathroom* / *All Bathrooms* for clarity.
- The villa pill reads **VILLA C3** with no owner name (the client is a company,
  PT Alchemy Estate Group). Tell us if an owner name should appear.
- "The Sanctuary" estate name is inferred from the C-block convention (not in the agreement).

## Structure
Everything lives in **`index.html`** — HTML, CSS, and JS in one file, no build step and no
dependencies (fonts load from Google Fonts).

- **`ITEMS`** — the inventory (133 rows): `{ cat, name, location, status, qty, prevBrand, newBrand, note? }`
  - `status`: `"Upgrade"` (gold ribbon, prev → new brand), `"New"` (green ribbon), `"As Is"`.
- **`BRANDED`** — shared custom-branding catalog (In-Room Amenities + Signage) with
  material/finish/dimension specs and Google Drive asset links.

Counts: **133 total · 28 upgraded · 41 new · 64 retained**, plus 21 branding assets.

## Run locally
```bash
python3 -m http.server 4173      # then open http://localhost:4173
```

## Deploy
No build step — fully static. Import the repo at vercel.com/new (Framework: **Other**, no
build command), or run `npx vercel --prod`.

## Notes
- The source agreements (furnishing, construction, PM consulting) are git-ignored.
- "Last updated" shows the current month automatically.
