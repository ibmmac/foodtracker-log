# Foodtracker log

Private daily food diary. Each day lives under `days/YYYY-MM-DD/` with:

- `README.md` — human-readable daily summary
- `day.json` — machine-readable totals and items
- `photos/` — package / label photos
- `items/<id>/` — per-food `item.json` (nutrition facts + barcode) and photo copy

## Barcodes

UPC-A barcodes are stored on each item when visible on the package photo. Missing barcodes are marked in `item.json` as `barcode_status`.

## Latest day

See [days/2026-09-17/](days/2026-09-17/).
