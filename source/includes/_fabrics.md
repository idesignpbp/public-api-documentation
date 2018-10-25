# Fabrics API

## Get All Collections

```shell
curl "https://api.trinity-apparel.com/v1/collections"
  -H "AUTHENTICATION Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 2,
        "name": "07 FW Bellagio",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_FW_Bellagio",
        "garment_type": 711,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 3,
        "name": "07 FW Governors",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_FW_Governors",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 4,
        "name": "07 FW Heritage Classic",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_FW_Heritage_Classic",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 5,
        "name": "07 FW Heritage Fashion",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_FW_Heritage_Fashion",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 6,
        "name": "07 FW Kensington I",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_FW_Kensington_I",
        "garment_type": 711,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": true,
        "is_live": true,
        "is_saks": false
    },
    {
        "id": 7,
        "name": "07 FW Kensington II",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_FW_Kensington_II",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 8,
        "name": "07 FW Lords",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_FW_Lords",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 9,
        "name": "07 FW Trofeo",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_FW_Trofeo",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 10,
        "name": "07 FW Zenith Cashmere",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_FW_Zenith_Cashmere",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 11,
        "name": "07 SS Cambridge",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_SS_Cambridge",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 12,
        "name": "07 SS Governors",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_SS_Governors",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 13,
        "name": "07 SS Heritage Classic",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_SS_Heritage_Classic",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 14,
        "name": "07 SS Heritage Fashion",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_SS_Heritage_Fashion",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 15,
        "name": "07 SS Lords",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_SS_Lords",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 16,
        "name": "07 SS Queensborough",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_SS_Queensborough",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 17,
        "name": "07 SS Thomas",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_SS_Thomas",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 18,
        "name": "07 SS Yorkshire",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_SS_Yorkshire",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 19,
        "name": "07 SS Zenith",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "07_SS_Zenith",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 20,
        "name": "08 SS Barberis",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "08_SS_Barberis",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 21,
        "name": "08 SS Florence Cottons",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "08_SS_Florence_Cottons",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 22,
        "name": "08 SS Florence Gabardines",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "08_SS_Florence_Gabardines",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 23,
        "name": "08 SS Heritage I",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "08_SS_Heritage_I",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 24,
        "name": "08 SS Heritage II",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "08_SS_Heritage_II",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 25,
        "name": "08 SS Jamison Fancies",
        "scene7_repeat": 0,
        "description": null,
        "collection_key": "08_SS_Jamison_Fancies",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    },
    {
        "id": 26,
        "name": "08 SS Jamison Flannels",
        "scene7_repeat": 0,
        "description": "The insignificant reflection of light gives this pale-contrast flannel a timeless gravity. Although this high-quality worsted is not heavy, it is the sign of a meditated purchase, a goal achieved, never of an impulsive action. It demands self-control, and offers authority in exchange. This flannel is for those in influential roles and who have an independent temperament and can be interpreted as an expression of experience and clarity of thought.",
        "collection_key": "08_SS_Jamison_Flannels",
        "garment_type": 199,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": false,
        "is_live": false,
        "is_saks": false
    }
]
```

Returns an array of fabric collections.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/collections`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
is_active | true | If set to true, the result will only include active fabrics

### Other

- Permissions: All
- Pagination: Yes

## Get All Fabrics

```shell
curl "https://api.trinity-apparel.com/v1/fabrics"
  -H "AUTHENTICATION Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 1,
        "active": true,
        "supplier_fabric_num": "CMT",
        "trinity_fabric_num": "CMT-70001",
        "in_stock": 1,
        "restock_date": null,
        "description": "CMT Fabric",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=CMT-70001"
    },
    {
        "id": 20,
        "active": false,
        "supplier_fabric_num": "486.341/12",
        "trinity_fabric_num": "W-70020",
        "in_stock": 1,
        "restock_date": null,
        "description": "Black Herringbone",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=W-70020"
    },
    {
        "id": 21,
        "active": false,
        "supplier_fabric_num": "ABCDE",
        "trinity_fabric_num": "C-70021",
        "in_stock": 1,
        "restock_date": null,
        "description": "test",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C-70021"
    },
    {
        "id": 22,
        "active": false,
        "supplier_fabric_num": "MBC061B",
        "trinity_fabric_num": "F-70022",
        "in_stock": 0,
        "restock_date": null,
        "description": "Navy, black mix w/ muted windowpane",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=F-70022"
    },
    {
        "id": 23,
        "active": false,
        "supplier_fabric_num": "MBC061B",
        "trinity_fabric_num": "F-70023",
        "in_stock": 0,
        "restock_date": null,
        "description": "Navy, black mix w/ muted windowpane",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=F-70023"
    },
    {
        "id": 24,
        "active": false,
        "supplier_fabric_num": "MBC061B",
        "trinity_fabric_num": "F-70024",
        "in_stock": 0,
        "restock_date": null,
        "description": "Navy, black mix w/ muted windowpane",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=F-70024"
    },
    {
        "id": 25,
        "active": false,
        "supplier_fabric_num": "MBC061B",
        "trinity_fabric_num": "F-70025",
        "in_stock": 0,
        "restock_date": null,
        "description": "Navy, black mix w/ muted windowpane",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=F-70025"
    },
    {
        "id": 26,
        "active": false,
        "supplier_fabric_num": "MC267B",
        "trinity_fabric_num": "A-70026",
        "in_stock": 0,
        "restock_date": null,
        "description": "NAVY SOLID",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=A-70026"
    },
    {
        "id": 27,
        "active": false,
        "supplier_fabric_num": "MC267A",
        "trinity_fabric_num": "A-70027",
        "in_stock": 1,
        "restock_date": null,
        "description": "BROWN MIX SOLID",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=A-70027"
    },
    {
        "id": 28,
        "active": false,
        "supplier_fabric_num": "MC257",
        "trinity_fabric_num": "A-70028",
        "in_stock": 0,
        "restock_date": null,
        "description": "NAVY STRIPE",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=A-70028"
    },
    {
        "id": 29,
        "active": false,
        "supplier_fabric_num": "MB195G",
        "trinity_fabric_num": "A-70029",
        "in_stock": 1,
        "restock_date": null,
        "description": "GUN METAL GRAY",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=A-70029"
    },
    {
        "id": 30,
        "active": false,
        "supplier_fabric_num": "MBC052B",
        "trinity_fabric_num": "B-70030",
        "in_stock": 0,
        "restock_date": null,
        "description": "GRAY CREPE",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=B-70030"
    },
    {
        "id": 31,
        "active": false,
        "supplier_fabric_num": "MB068A",
        "trinity_fabric_num": "B-70031",
        "in_stock": 0,
        "restock_date": null,
        "description": "NAVY GABARDINE",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=B-70031"
    },
    {
        "id": 32,
        "active": false,
        "supplier_fabric_num": "MC512",
        "trinity_fabric_num": "B-70032",
        "in_stock": 1,
        "restock_date": null,
        "description": "BROWN AND BURGUNDY CREPE",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=B-70032"
    },
    {
        "id": 33,
        "active": false,
        "supplier_fabric_num": "MC255E",
        "trinity_fabric_num": "B-70033",
        "in_stock": 1,
        "restock_date": null,
        "description": "TAN GRAY MIX",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=B-70033"
    },
    {
        "id": 34,
        "active": false,
        "supplier_fabric_num": "MBC052A",
        "trinity_fabric_num": "B-70034",
        "in_stock": 0,
        "restock_date": null,
        "description": "DARK OLIVE FANCY",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=B-70034"
    },
    {
        "id": 35,
        "active": false,
        "supplier_fabric_num": "MB104A",
        "trinity_fabric_num": "B-70035",
        "in_stock": 0,
        "restock_date": null,
        "description": "NAVY STRIPE",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=B-70035"
    },
    {
        "id": 36,
        "active": false,
        "supplier_fabric_num": "MB29200",
        "trinity_fabric_num": "J-70036",
        "in_stock": 1,
        "restock_date": null,
        "description": "GRAY MINI HERRINGBONE",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=J-70036"
    },
    {
        "id": 37,
        "active": false,
        "supplier_fabric_num": "MB104B",
        "trinity_fabric_num": "B-70037",
        "in_stock": 1,
        "restock_date": null,
        "description": "CHARCOAL STRIPE",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=B-70037"
    },
    {
        "id": 38,
        "active": false,
        "supplier_fabric_num": "MB255",
        "trinity_fabric_num": "J-70038",
        "in_stock": 0,
        "restock_date": null,
        "description": "TAN MINI CHECK",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=J-70038"
    },
    {
        "id": 39,
        "active": false,
        "supplier_fabric_num": "MB104F",
        "trinity_fabric_num": "B-70039",
        "in_stock": 0,
        "restock_date": null,
        "description": "BLACK PLAIN WEAVE",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=B-70039"
    },
    {
        "id": 40,
        "active": false,
        "supplier_fabric_num": "MB052B0",
        "trinity_fabric_num": "K-70040",
        "in_stock": 1,
        "restock_date": null,
        "description": "BLUE GRAY GABARDINE",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=K-70040"
    },
    {
        "id": 41,
        "active": false,
        "supplier_fabric_num": "MB068B",
        "trinity_fabric_num": "B-70041",
        "in_stock": 1,
        "restock_date": null,
        "description": "GRAY HIGH TWIST",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=B-70041"
    },
    {
        "id": 42,
        "active": false,
        "supplier_fabric_num": "MB104C",
        "trinity_fabric_num": "B-70042",
        "in_stock": 1,
        "restock_date": null,
        "description": "GRAY PLAIN WEAVE",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=B-70042"
    },
    {
        "id": 43,
        "active": false,
        "supplier_fabric_num": "MBC058A",
        "trinity_fabric_num": "C-70043",
        "in_stock": 0,
        "restock_date": null,
        "description": "BROWN AND TAN HERRINGBONE",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C-70043"
    }
]
```

Returns an array of fabrics.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/fabrics`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
collection_id | N/A | Only return fabrics from a specific collection
trinity_fabric_num | N/A | Show fabrics that match a specific Trinity fabric number
supplier_fabric_num | N/A | Show fabrics that match a specific Supplier fabric number
is_active | true | If set to true, the result will only include active fabrics

### Other

- Permissions: All
- Pagination: Yes

## Get a Specific Fabric

```shell
curl "https://api.trinity-apparel.com/v1/fabrics/39001"
  -H "AUTHENTICATION Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
    "id": 39001,
    "active": true,
    "supplier_id": 49,
    "fabric_mill_id": 60,
    "label_id": 19,
    "supplier_fabric_num": "54557-18",
    "trinity_fabric_num": "Z8-3339001",
    "country_origin": "Italy",
    "fabric_weight_grams_meter": 105,
    "fabric_grouping": "blue",
    "secondary_fabric_grouping": null,
    "pattern": "Foulards/Neats",
    "fabric_width": "58.0",
    "cuttable_width": "58.0",
    "grain_repeat": null,
    "crosswise_repeat": null,
    "one_way_nap": false,
    "horiz_pattern": false,
    "non_iron": false,
    "supplier_price_dollars_meter": "33.54",
    "supplier_price_dollars_yard": "30.67",
    "in_stock": 1,
    "restock_date": null,
    "sub_supplier_id": null,
    "sub_fabric_num": null,
    "rapid_replenishment": false,
    "last_stock_edit_date": "2017-02-27T16:43:46.000Z",
    "fabric_price_code_id": 142,
    "fabric_composition_id": 13,
    "fabric_garment_type": 8,
    "trim_garment_type": 0,
    "fabric_usage": 1,
    "premium_id": 1,
    "fabric_season": 33,
    "fabric_year": 2017,
    "luxury_level_id": 24,
    "material_type_id": 12,
    "base_color": null,
    "deco_color_1": null,
    "deco_color_2": null,
    "panel": 0,
    "panel_row": 1,
    "panel_column": 1,
    "description": "Midnight Pin Dot",
    "created_at": "2017-02-27T16:43:46.000Z",
    "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3339001",
    "collection": {
        "id": 1338,
        "name": "Thomas Mason Seasonal V17031",
        "scene7_repeat": 0,
        "description": "To get you through the warmer months, we’ve sourced a seasonal range of fabrics from Thomas Mason for the Spring/Summer season. This collection features an array of designs in a fresh spring palette.",
        "collection_key": "Thomas_Mason_Seasonal_V17031",
        "garment_type": 8,
        "trim_garment_type": 0,
        "fabrics_per_row": 2,
        "rows_per_panel": 12,
        "is_demo": true,
        "is_live": true,
        "is_saks": false
    }
}
```

Returns details on a specific fabric.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/fabrics/:fabric_id`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
fabric_id | N/A | The specific fabric id you want to see

### Other

- Permissions: All
- Pagination: N/A