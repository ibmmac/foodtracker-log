# Foodtracker log — standing requirements

Private daily food diary for Mitch. These rules apply to every day under `days/YYYY-MM-DD/`.

## 1. Daily calorie goal

- Default daily calorie goal: **1500 kcal** (`goal_kcal` in `day.json`).
- After any logging update, each day MUST show:
  - calories consumed
  - **remaining kcal** (`goal_kcal − calories`)
  - **% of goal remaining** and % used
- Surface these numbers in both `day.json` totals and the day `README.md`.

## 2. Barcode → online product image (mandatory)

When a food item has a known barcode (UPC-A / EAN-13):

- The repo **MUST** store the **official / matching online product image** for that UPC (retailer product listing preferred: BJ’s, Walmart, Target, manufacturer, Open Food Facts, Instacart, etc.).
- **Do not** use the user’s phone photos of the package as the primary `photo`.
- User/package photos are only for **reading labels and barcodes during logging** (optional secondary `barcode_photo`).
- Each item with a product photo MUST include `photo_credit` with at least:
  - `source` / `retailer` / `url` (product or image page)
  - `image_url` when known
  - `license` / notes if available

If no barcode is available (e.g. loose snack with no package photo), set `photo` to `null` and `barcode_status` to `no_photo` — do **not** invent a barcode or fake product image.

## 3. Day folder layout

Each day under `days/YYYY-MM-DD/` has:

| Path | Purpose |
|------|---------|
| `README.md` | Human-readable summary (goal, remaining %, table, per-item sections) |
| `day.json` | Machine-readable totals + full item list |
| `photos/` | Day-level photos (primary = online product images) |
| `items/<id>/item.json` | Per-food facts, barcode, logged macros, photo paths |
| `items/<id>/<id>.jpg` | Copy of the primary product photo |

## 4. `item.json` fields

Each item SHOULD include:

- `id`, `name`, `brand`
- `barcode` (UPC-A when known) and `barcode_format`
- `nutrition_per_serving` and `logged` macros (calories, protein_g, carbs_g, fat_g)
- `photo` (path to online product image, or `null`)
- `photo_credit` (required when `photo` is an online product image)
- Optional: `barcode_photo` for the user label/barcode shot used while logging
- Optional: `barcode_status` when barcode/photo is missing (`no_photo`)

## 5. GitHub sync

After logging changes:

1. Commit with a clear message describing what changed.
2. **Push to `main`** on GitHub (`ibmmac/foodtracker-log`).
3. Do **not** force-push.

## Image workflow (when barcode is known)

1. Look up the UPC (Open Food Facts `https://world.openfoodfacts.org/api/v2/product/{ean13}.json`, upcitemdb, retailer sites).
2. Download the retailer/manufacturer product image.
3. Resize to max width **1280** JPEG.
4. Place as `photos/<id>.jpg` and `items/<id>/<id>.jpg`.
5. Set `photo` + `photo_credit`; keep nutrition and logged amounts unchanged unless the label says otherwise.
