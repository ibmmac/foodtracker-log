# Product catalog

Shared database of foods. Product photos and nutrition live **once** here; day logs only reference `catalog_id`.

**9 items** · Machine-readable: [`index.json`](index.json)

| Photo | Name | Brand | Barcode / ID | kcal/serving | Folder |
|-------|------|-------|--------------|--------------|--------|
| ![](items/038900772208/product.jpg) | [Dole Fruit Bowls Snacks](items/038900772208/) | Dole | `038900772208` | 70 | [`038900772208`](items/038900772208/) |
| ![](items/046025202462/product.jpg) | [Easy Eggs Peeled Hard Cooked Eggs](items/046025202462/) | Easy Eggs / Michael Foods | `046025202462` | 60 | [`046025202462`](items/046025202462/) |
| ![](items/074030656209/product.jpg) | [Galbani Reduced Fat Cheese Sticks](items/074030656209/) | Galbani / Lactalis American Group | `074030656209` | 60 | [`074030656209`](items/074030656209/) |
| ![](items/078742237855/product.jpg) | [Great Value Sardines in Water](items/078742237855/) | Great Value / Walmart | `078742237855` | 100 | [`078742237855`](items/078742237855/) |
| ![](items/888670012864/product.jpg) | [Wellsley Farms Homestyle Potato Salad](items/888670012864/) | Wellsley Farms / BJ's Wholesale Club | `888670012864` | 190 | [`888670012864`](items/888670012864/) |
| ![](items/888670012901/product.jpg) | [Wellsley Farms Aegean Greek Pasta](items/888670012901/) | Wellsley Farms / BJ's Wholesale Club | `888670012901` | 390 | [`888670012901`](items/888670012901/) |
| ![](items/888670053638/product.jpg) | [Wellsley Farms Gala Apples](items/888670053638/) | Wellsley Farms / BJ's Wholesale Club | `888670053638` | 95 | [`888670053638`](items/888670053638/) |
| — | [Fasted breakfast](items/id-fasted-breakfast/) | — | `id-fasted-breakfast` | 0 | [`id-fasted-breakfast`](items/id-fasted-breakfast/) |
| — | [Teriyaki beef stick](items/id-teriyaki-beef-stick/) | Unknown (estimated as Jack Link's Teriyaki style) | `id-teriyaki-beef-stick` | 110 | [`id-teriyaki-beef-stick`](items/id-teriyaki-beef-stick/) |

## Layout

```
catalog/
  index.json          # machine-readable list
  README.md           # this page
  items/<catalog_id>/
    item.json
    product.jpg       # online product image when barcode known
    barcode-label.jpg # optional user label shot
```

`catalog_id` is the UPC when known, otherwise `id-<slug>`.

