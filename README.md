# Foodtracker log

Private daily food diary. Each day lives under `days/YYYY-MM-DD/` with:

- `README.md` — human-readable daily summary
- `day.json` — machine-readable totals and items
- `photos/` — **online product images** for barcoded items (not user phone photos)
- `items/<id>/` — per-food `item.json` (nutrition facts + barcode) and product photo copy

## Standing rules

See **[REQUIREMENTS.md](REQUIREMENTS.md)** for the full standing requirements, including:

1. Default daily calorie goal **1500 kcal**, with remaining kcal and % of goal remaining after every update
2. When a barcode is known, store the matching **online product image** for that UPC (user photos are only for reading labels during logging)
3. Day folder layout (`README.md`, `day.json`, `photos/`, `items/<id>/`)
4. Required `item.json` fields (`barcode`, nutrition, logged macros, `photo`, `photo_credit`)
5. Push to GitHub `main` after logging changes

## Barcodes

UPC-A barcodes are stored on each item when known. Missing barcodes are marked as `barcode_status: no_photo` with `photo: null`.

## Goal

Default daily calorie goal: **1500 kcal**. Each day README shows calories left and % of goal remaining.

## Latest day

See [days/2026-09-18/](days/2026-09-18/).
