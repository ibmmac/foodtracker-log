# Catalog enrichment report

**Date:** 2026-09-18 (America/New_York)
**Repo:** foodtracker-log / `catalog/`

## Summary

| Metric | Before | After |
|--------|--------|-------|
| Total catalog items | 88 | 88 |
| Incomplete (missing calories OR serving_size OR UPC-without-photo) | 46 | **0** |

## What changed

### UPC photos + credits
- `041800207503` Welch's grape juice — OFF `product.jpg` + photo_credit
- `052000103120` Gatorade Frost Glacier Cherry — Target Scene7 `product.jpg` + photo_credit; nutrition set to 80 kcal / 12 fl oz label
- `088702015607` Bonne Maman strawberry — OFF `product.jpg` + photo_credit
- `078742279091` GV purified water — OFF `product.jpg` + photo_credit; calories **0**
- `044000046545` Newtons fig bars — photo_credit added (jpg already present)
- `681131387538` Marketside romaine — photo_credit added (jpg already present)
- `078742141404` GV organic marinara — brand set to Great Value / Walmart

### UPC migrations (confident OFF matches only)
- `id-great-value-honey-graham-crackers-14-4-oz-3-count` → **`078742072531`** (with product.jpg)
- `id-great-value-organic-tomato-ketchup-20-oz` → **`078742136424`** (with product.jpg)
- No day entries referenced the old ids (safe rename).

### Produce (USDA FoodData Central estimates)
Filled serving_size + nutrition for cucumber, gala apples, Hass avocado, mandarins (2), mini cucumbers (2), baby carrots (2), strawberries, portabella, white mushrooms, bananas. `barcode` null, `barcode_status` no_photo.

### Branded id-* (nutrition filled; UPC not invented)
Chobani (2), Festive ground turkey, remaining Great Value SKUs, Jennie-O turkey dogs, Kellogg's variety pack, Liquid I.V., Parmalat milk, Snickers/M&M's/Twix fun-size, SweeTARTS party mix. Notes mark estimates where label UPC was unresolved.

### Other
- `id-fasted-breakfast`: serving_size set; calories remain **0**
- Rebuilt `catalog/index.json` and `catalog/README.md`

## Remaining gaps

**None** for the incomplete criteria (calories / serving_size / UPC-without-photo).

Soft follow-ups (not counted incomplete): many branded `id-*` items still lack a verified UPC/photo — resolve from package barcode when available and migrate folders.

## Actions log

- UPC 041800207503: added product.jpg + photo_credit
- UPC 088702015607: added product.jpg + photo_credit
- UPC 078742279091: added product.jpg + photo_credit + nutrition
- UPC 052000103120: added product.jpg + photo_credit + nutrition
- UPC 044000046545: added photo_credit
- UPC 681131387538: added photo_credit
- 078742141404: set brand Great Value / Walmart
- MIGRATED id-great-value-honey-graham-crackers-14-4-oz-3-count -> 078742072531
- MIGRATED id-great-value-organic-tomato-ketchup-20-oz -> 078742136424
- PRODUCE id-fresh-cucumber-each: USDA nutrition filled
- PRODUCE id-fresh-gala-apples-3-lb-bag: USDA nutrition filled
- PRODUCE id-fresh-hass-avocados-each: USDA nutrition filled
- PRODUCE id-fresh-mandarin-oranges: USDA nutrition filled
- PRODUCE id-fresh-mandarin-oranges-3-lb-bag-naturally-ripened: USDA nutrition filled
- PRODUCE id-fresh-mini-cucumbers: USDA nutrition filled
- PRODUCE id-fresh-organic-mini-cucumbers-16-oz: USDA nutrition filled
- PRODUCE id-fresh-produce-baby-peeled-carrots-1lb-bag: USDA nutrition filled
- PRODUCE id-organic-marketside-fresh-baby-peeled-carrots-1-lb: USDA nutrition filled
- PRODUCE id-fresh-usda-organic-strawberries-1-lb-container: USDA nutrition filled
- PRODUCE id-fresh-whole-portabella-mushroom-caps-6-oz: USDA nutrition filled
- PRODUCE id-fresh-whole-white-mushrooms: USDA nutrition filled
- PRODUCE id-marketside-fresh-organic-bananas-bunch: USDA nutrition filled
- id-fasted-breakfast: serving_size + zero nutrition
- BRANDED id-chobani-low-fat-vanilla-greek-yogurt-mixed-berry-o: nutrition filled (no UPC)
- BRANDED id-chobani-nonfat-greek-key-lime: nutrition filled (no UPC)
- BRANDED id-festive-ground-turkey-frozen-1-lb-roll: nutrition filled (no UPC)
- BRANDED id-great-value-100-pure-beef-burgers-85-lean-15-fat-3: nutrition filled (no UPC)
- BRANDED id-great-value-canned-pineapple-chunks-in-pineapple-j: nutrition filled (no UPC)
- BRANDED id-great-value-dry-roasted-and-unsalted-peanuts-16-oz: nutrition filled (no UPC)
- BRANDED id-great-value-extra-sharp-whole-white-cheddar-cheese: nutrition filled (no UPC)
- BRANDED id-great-value-fat-free-turkey-breast-16-oz-bag-slice: nutrition filled (no UPC)
- BRANDED id-great-value-honey-ham-lunchmeat-plastic-tub-9-oz: nutrition filled (no UPC)
- BRANDED id-great-value-hot-dog-buns-white-11-oz-8-count: nutrition filled (no UPC)
- BRANDED id-great-value-large-pitted-black-olives-6-oz: nutrition filled (no UPC)
- BRANDED id-great-value-organic-lentils-15-oz-can: nutrition filled (no UPC)
- BRANDED id-great-value-organic-roasted-garlic-pasta-sauce-24: nutrition filled (no UPC)
- BRANDED id-great-value-organic-yellow-mustard-8-oz: nutrition filled (no UPC)
- BRANDED id-great-value-swiss-deli-style-sliced-cheese-8-oz-pa: nutrition filled (no UPC)
- BRANDED id-great-value-turkey-pepperoni-slices-5-oz: nutrition filled (no UPC)
- BRANDED id-great-value-unsweetened-applesauce-50oz: nutrition filled (no UPC)
- BRANDED id-jennie-o-turkey-hot-dogs-40-less-fat-refrigerated: nutrition filled (no UPC)
- BRANDED id-kellogg-s-breakfast-cereal-kids-cereal-family-brea: nutrition filled (no UPC)
- BRANDED id-liquid-i-v-orange-vanilla-dream-hydration-multipli: nutrition filled (no UPC)
- BRANDED id-parmalat-whole-milk-32-fl-oz: nutrition filled (no UPC)
- BRANDED id-snickers-m-m-s-twix-fun-size-chocolate-candy-varie: nutrition filled (no UPC)
- BRANDED id-sweetarts-variety-party-mix-individually-wrapped-a: nutrition filled (no UPC)
- Rebuilt index.json (88 items)
- Rebuilt catalog/README.md
