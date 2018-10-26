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
        "id": 1309,
        "name": "Derby Performance Cornerstone Suitings V17011"
    },
    {
        "id": 1312,
        "name": "Sartorial Dress V17011"
    },
    {
        "id": 1317,
        "name": "Derby Performance Contemporary Suitings V17011"
    },
    {
        "id": 1318,
        "name": "Kensington Brighton Sport Coats V17011"
    },
    {
        "id": 1319,
        "name": "Dormeuil Iconik Nano 704 V17011"
    },
    {
        "id": 1320,
        "name": "Dormeuil Amadeus Jacketings 365 No.702 V17011"
    },
    {
        "id": 1321,
        "name": "Sartorial Volume 1 V17011"
    },
    {
        "id": 1322,
        "name": "Derby Performance Corinthian Sport Coats V17011"
    },
    {
        "id": 1323,
        "name": "Zenith Riviera V17011"
    },
    {
        "id": 1324,
        "name": "Norwich TravelEase V17011"
    },
    {
        "id": 1325,
        "name": "Dormeuil 703 D Philosphy V17011V"
    },
    {
        "id": 1326,
        "name": "Dormeuil 705 Distinction V17011V"
    },
    {
        "id": 1327,
        "name": "Lifestyle V17031"
    },
    {
        "id": 1328,
        "name": "Puro Colors V17031"
    },
    {
        "id": 1329,
        "name": "Puro Stripes & Checks V17031"
    },
    {
        "id": 1330,
        "name": "Puro White Blue V17031"
    },
    {
        "id": 1331,
        "name": "Ghost"
    },
    {
        "id": 1332,
        "name": "Bedlam 461 V17021V"
    },
    {
        "id": 1333,
        "name": "Classic ll 477E V17021V"
    },
    {
        "id": 1334,
        "name": "Fresco lll 492 V17021V"
    },
    {
        "id": 1335,
        "name": "QX² 494 V17021V"
    },
    {
        "id": 1336,
        "name": "QZ Project 411-A V17021V"
    },
    {
        "id": 1337,
        "name": "Worsted Alsport ll 458 V17021V"
    },
    {
        "id": 1338,
        "name": "Thomas Mason Seasonal V17031"
    },
    {
        "id": 1339,
        "name": "Marzoni M1 V17031V"
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

## Get a Specific Collection

```shell
curl "https://api.trinity-apparel.com/v1/collections/1854"
  -H "AUTHENTICATION Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
    "id": 1854,
    "name": "Outerwear V18082",
    "description": "",
    "fabrics": [
        {
            "id": 54875,
            "active": false,
            "in_stock": 1,
            "restock_date": null,
            "description": "Blue Navy Plaid",
            "supplier_fabric_number": "BT65151-1",
            "trinity_fabric_number": "C4-3754875",
            "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754875",
            "inventory_status": "In Stock"
        },
        {
            "id": 54876,
            "active": false,
            "in_stock": 1,
            "restock_date": null,
            "description": "Charcoal Black Plaid",
            "supplier_fabric_number": "BT65151-2",
            "trinity_fabric_number": "C4-3754876",
            "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754876",
            "inventory_status": "In Stock"
        },
        {
            "id": 54877,
            "active": false,
            "in_stock": 1,
            "restock_date": null,
            "description": "Black White Herringbone",
            "supplier_fabric_number": "BT65139-1",
            "trinity_fabric_number": "C4-3754877",
            "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754877",
            "inventory_status": "In Stock"
        },
        {
            "id": 54878,
            "active": false,
            "in_stock": 1,
            "restock_date": null,
            "description": "Blue Navy Herringbone",
            "supplier_fabric_number": "BT65139-3",
            "trinity_fabric_number": "C4-3754878",
            "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754878",
            "inventory_status": "In Stock"
        },
        {
            "id": 54879,
            "active": false,
            "in_stock": 1,
            "restock_date": null,
            "description": "Grey Charcoal Herringbone",
            "supplier_fabric_number": "BT65139-5",
            "trinity_fabric_number": "C4-3754879",
            "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754879",
            "inventory_status": "In Stock"
        },
        {
            "id": 54880,
            "active": false,
            "in_stock": 1,
            "restock_date": null,
            "description": "Grey Charcoal Twill",
            "supplier_fabric_number": "BT65153-7",
            "trinity_fabric_number": "C4-3754880",
            "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754880",
            "inventory_status": "In Stock"
        },
        {
            "id": 54881,
            "active": false,
            "in_stock": 1,
            "restock_date": null,
            "description": "Brown Black Twill",
            "supplier_fabric_number": "BT65153-10",
            "trinity_fabric_number": "C4-3754881",
            "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754881",
            "inventory_status": "In Stock"
        },
        {
            "id": 54882,
            "active": false,
            "in_stock": 1,
            "restock_date": null,
            "description": "Blue Navy Twill",
            "supplier_fabric_number": "BT65153-11",
            "trinity_fabric_number": "C4-3754882",
            "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754882",
            "inventory_status": "In Stock"
        },
        {
            "id": 54883,
            "active": false,
            "in_stock": 1,
            "restock_date": null,
            "description": "Charcoal Grey Expanded Plaid",
            "supplier_fabric_number": "340028",
            "trinity_fabric_number": "Z6-3754883",
            "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z6-3754883",
            "inventory_status": "In Stock"
        },
        {
            "id": 54884,
            "active": false,
            "in_stock": 1,
            "restock_date": null,
            "description": "Navy  Expanded Herringbone",
            "supplier_fabric_number": "340032",
            "trinity_fabric_number": "Z6-3754884",
            "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z6-3754884",
            "inventory_status": "In Stock"
        },
        {
            "id": 54885,
            "active": false,
            "in_stock": 1,
            "restock_date": null,
            "description": "Grey Expanded Herringbone",
            "supplier_fabric_number": "340031",
            "trinity_fabric_number": "Z6-3754885",
            "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z6-3754885",
            "inventory_status": "In Stock"
        },
        {
            "id": 54886,
            "active": false,
            "in_stock": 1,
            "restock_date": null,
            "description": "Navy Blue Basket",
            "supplier_fabric_number": "601 574 900",
            "trinity_fabric_number": "Z4-3754886",
            "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3754886",
            "inventory_status": "In Stock"
        },
        {
            "id": 54887,
            "active": false,
            "in_stock": 1,
            "restock_date": null,
            "description": "Red Charcoal Check",
            "supplier_fabric_number": "665 102 1500",
            "trinity_fabric_number": "Z6-3754887",
            "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z6-3754887",
            "inventory_status": "In Stock"
        },
        {
            "id": 54888,
            "active": false,
            "in_stock": 1,
            "restock_date": null,
            "description": "Blue Diamond",
            "supplier_fabric_number": "665 104 1500",
            "trinity_fabric_number": "Z6-3754888",
            "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z6-3754888",
            "inventory_status": "In Stock"
        }
    ]
}
```

Returns details on a fabric collection and a list of all fabrics in that collection.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/collections/:id`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
id | N/A | The specific collection id you want to see

### Other

- Permissions: All
- Pagination: N/A

## Get All Fabrics

```shell
curl "https://api.trinity-apparel.com/v1/fabrics"
  -H "AUTHENTICATION Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 32461,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Sky Blue Copper Track Windowpane",
        "supplier_fabric_number": "641 014 900",
        "trinity_fabric_number": "Z4-3332461",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332461",
        "inventory_status": "In Stock"
    },
    {
        "id": 32462,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Char Blue Brick Track Windowpane",
        "supplier_fabric_number": "641 028 900",
        "trinity_fabric_number": "Z4-3332462",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332462",
        "inventory_status": "In Stock"
    },
    {
        "id": 32463,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Plaid",
        "supplier_fabric_number": "641 104 900",
        "trinity_fabric_number": "Z4-3332463",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332463",
        "inventory_status": "In Stock"
    },
    {
        "id": 32464,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Char Blue Merlot Plaid",
        "supplier_fabric_number": "641 099 900",
        "trinity_fabric_number": "Z4-3332464",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332464",
        "inventory_status": "In Stock"
    },
    {
        "id": 32465,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Tan Navy Check",
        "supplier_fabric_number": "609 033 900",
        "trinity_fabric_number": "Z4-3332465",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332465",
        "inventory_status": "In Stock"
    },
    {
        "id": 32466,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Blue Brown Check",
        "supplier_fabric_number": "609 032 900",
        "trinity_fabric_number": "Z4-3332466",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332466",
        "inventory_status": "In Stock"
    },
    {
        "id": 32467,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Gray Windowpane",
        "supplier_fabric_number": "641 030 900",
        "trinity_fabric_number": "Z4-3332467",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332467",
        "inventory_status": "In Stock"
    },
    {
        "id": 32468,
        "active": true,
        "in_stock": 0,
        "restock_date": "",
        "description": "Gray Navy Windowpane",
        "supplier_fabric_number": "641 029 900",
        "trinity_fabric_number": "Z4-3332468",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332468",
        "inventory_status": "Unknown"
    },
    {
        "id": 32469,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Brown Aqua Track Windowpane",
        "supplier_fabric_number": "641 012 900",
        "trinity_fabric_number": "Z4-3332469",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332469",
        "inventory_status": "In Stock"
    },
    {
        "id": 32470,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Gray Tan Track Windowpane",
        "supplier_fabric_number": "641 010 900",
        "trinity_fabric_number": "Z4-3332470",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332470",
        "inventory_status": "In Stock"
    },
    {
        "id": 32471,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Red Track Windowpane",
        "supplier_fabric_number": "641 011 900",
        "trinity_fabric_number": "Z4-3332471",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332471",
        "inventory_status": "In Stock"
    },
    {
        "id": 32472,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Crimson Gray Track Windowpane",
        "supplier_fabric_number": "641 050 900",
        "trinity_fabric_number": "Z4-3332472",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332472",
        "inventory_status": "In Stock"
    },
    {
        "id": 32473,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Brick Tan Track Windowpane",
        "supplier_fabric_number": "641 041 900",
        "trinity_fabric_number": "Z4-3332473",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332473",
        "inventory_status": "In Stock"
    },
    {
        "id": 32474,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Blue Tan Track Windowpane",
        "supplier_fabric_number": "641 042 900",
        "trinity_fabric_number": "Z4-3332474",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332474",
        "inventory_status": "In Stock"
    },
    {
        "id": 32475,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Brown Plaid",
        "supplier_fabric_number": "641 107 900",
        "trinity_fabric_number": "Z4-3332475",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332475",
        "inventory_status": "In Stock"
    },
    {
        "id": 32476,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Blue Plum Plaid",
        "supplier_fabric_number": "641 108 900",
        "trinity_fabric_number": "Z4-3332476",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332476",
        "inventory_status": "In Stock"
    },
    {
        "id": 32477,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Puple Gold Track Windowpane",
        "supplier_fabric_number": "641 049 900",
        "trinity_fabric_number": "Z4-3332477",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332477",
        "inventory_status": "In Stock"
    },
    {
        "id": 32478,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Royal Track Windowpane",
        "supplier_fabric_number": "641 047 900",
        "trinity_fabric_number": "Z4-3332478",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332478",
        "inventory_status": "In Stock"
    },
    {
        "id": 32479,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Green Rose Track Windowpane",
        "supplier_fabric_number": "641 048 900",
        "trinity_fabric_number": "Z4-3332479",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332479",
        "inventory_status": "In Stock"
    },
    {
        "id": 32480,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Char Blue Royal Windowpane",
        "supplier_fabric_number": "641 004 900",
        "trinity_fabric_number": "Z4-3332480",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332480",
        "inventory_status": "In Stock"
    },
    {
        "id": 32481,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Charcoal Crimson Windowpane",
        "supplier_fabric_number": "641 003 900",
        "trinity_fabric_number": "Z4-3332481",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332481",
        "inventory_status": "In Stock"
    },
    {
        "id": 32482,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Gray Purple Track Windopane",
        "supplier_fabric_number": "641 006 900",
        "trinity_fabric_number": "Z4-3332482",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332482",
        "inventory_status": "In Stock"
    },
    {
        "id": 32483,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Blue Plum Track Windowpane",
        "supplier_fabric_number": "641 007 900",
        "trinity_fabric_number": "Z4-3332483",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332483",
        "inventory_status": "In Stock"
    },
    {
        "id": 32484,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Silver Teal Track Windowpane",
        "supplier_fabric_number": "641 005 900",
        "trinity_fabric_number": "Z4-3332484",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332484",
        "inventory_status": "In Stock"
    },
    {
        "id": 32485,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Brown Navy Track Windowpane",
        "supplier_fabric_number": "641 016 900",
        "trinity_fabric_number": "Z4-3332485",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3332485",
        "inventory_status": "In Stock"
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
- Pagination: No

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
    "in_stock": 2,
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
    "fabric_year": 2016,
    "luxury_level_id": 24,
    "material_type_id": 12,
    "base_color": null,
    "deco_color_1": null,
    "deco_color_2": null,
    "panel": 1,
    "panel_row": 1,
    "panel_column": 1,
    "description": "Midnight Pin Dot",
    "created_at": "2017-02-27T16:43:46.000Z",
    "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3339001",
    "inventory_status": "Sold Out",
    "collection": {
        "id": 1338,
        "name": "Thomas Mason Seasonal V17031"
    }
}
```

Returns details on a specific fabric.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/fabrics/:id`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
id | N/A | The specific fabric id you want to see

### Other

- Permissions: All
- Pagination: N/A