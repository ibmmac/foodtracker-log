# Foodtracker log — standing requirements

Private daily food diary for Mitch. These rules apply to every update.

## 1. Daily calorie goal

- Default daily calorie goal: **1500 kcal** (`goal_kcal` in `day.json`).
- After any logging update, each day MUST show:
  - calories consumed
  - **remaining kcal** (`goal_kcal − calories`)
  - **% of goal remaining** and % used
- Surface these numbers in both `day.json` totals and the day `README.md`.

## 2. Shared product catalog (no per-day image copies)

Product identity, nutrition facts, barcodes, and **product photos** live once under:

```
catalog/items/<catalog_id>/
  item.json      # name, brand, barcode, nutrition_per_serving, photo_credit
  product.jpg    # online product image (when barcode known)
  barcode-label.jpg  # optional: user label shot used while logging
catalog/index.json
```

- **`catalog_id`** is the UPC barcode when known (e.g. `888670053638`), otherwise `id-<slug>` for items without a barcode.
- Day folders **MUST NOT** store copies of product images. Days only reference `catalog_id`.
- Eating the same product on multiple days reuses the same catalog entry.

## 3. Barcode → online product image (mandatory)

When a food item has a known barcode (UPC-A / EAN-13):

- The catalog **MUST** store the **official / matching online product image** for that UPC (retailer listing preferred).
- **Do not** use the user’s phone photos of the package as the primary `product.jpg`.
- User/package photos are only for **reading labels and barcodes during logging** (optional `barcode-label.jpg`).
- Each catalog item with a product photo MUST include `photo_credit` with source/retailer URL and `image_url` when known.

If no barcode is available, set `photo` to null and `barcode_status` to `no_photo` — do **not** invent a barcode or fake product image.

## 4. Day folder layout

Each day under `days/YYYY-MM-DD/` has **only**:

| Path | Purpose |
|------|---------|
| `README.md` | Human-readable summary (goal, remaining %, table linking to catalog) |
| `day.json` | Totals + `entries[]` that reference `catalog_id` and logged amounts |

No `photos/` or `items/` directories inside a day.

### `day.json` entry shape

```json
{
  "catalog_id": "888670053638",
  "catalog_path": "catalog/items/888670053638/",
  "name": "Wellsley Farms Gala Apples",
  "amount_eaten": "1 medium apple",
  "servings_eaten": 1,
  "logged": { "calories": 95, "protein_g": 0.5, "carbs_g": 25, "fat_g": 0.3 },
  "location": "home",
  "source": "usda_estimate"
}
```

## 5. Meal location (required)

For every meal or snack logged, ask Mitch **where it was eaten** and store it on the day entry:

- `home`
- `work`
- `other` (with a short free-text `location_note`, e.g. restaurant name)

Field on each `days/.../day.json` entry:

```json
"location": "home" | "work" | "other",
"location_note": "optional when location is other"
```

Do not skip this question when logging food.

## 6. GitHub sync

After logging changes:

1. Commit with a clear message describing what changed.
2. **Push to `main`** on GitHub (`ibmmac/foodtracker-log`).
3. Do **not** force-push.

## Image workflow (when barcode is known)

1. Look up the UPC (Open Food Facts, upcitemdb, retailer sites).
2. Download the retailer/manufacturer product image into `catalog/items/<barcode>/product.jpg` (max width 1280 JPEG) — only if that file is not already present.
3. Write/update `catalog/items/<barcode>/item.json` with nutrition + `photo_credit`.
4. Append a day `entries[]` row that references `catalog_id` (no image copy into the day folder).
