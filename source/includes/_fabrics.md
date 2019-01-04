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
        "id": 42701,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Teal Basket Weave",
        "supplier_fabric_number": "602 275 800",
        "trinity_fabric_number": "Z4-3642701",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3642701",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3642701&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42702,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Dark Teal Basket Weave",
        "supplier_fabric_number": "602 036 800",
        "trinity_fabric_number": "Z4-3642702",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3642702",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3642702&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42703,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Sky Blue Basket Weave",
        "supplier_fabric_number": "602 290 800",
        "trinity_fabric_number": "Z4-3642703",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3642703",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3642703&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42704,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Blue Basket Weave",
        "supplier_fabric_number": "602 285 800",
        "trinity_fabric_number": "Z4-3642704",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3642704",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3642704&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42705,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lt Lavender Basket Weave",
        "supplier_fabric_number": "602 032 800",
        "trinity_fabric_number": "Z4-3642705",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3642705",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3642705&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42706,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Bright Purple Basket Weave",
        "supplier_fabric_number": "602 279 800",
        "trinity_fabric_number": "Z4-3642706",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3642706",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3642706&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42707,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Maroon Basket Weave",
        "supplier_fabric_number": "602 047 800",
        "trinity_fabric_number": "Z4-3642707",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3642707",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3642707&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42708,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lavendar Blue Basket Weave",
        "supplier_fabric_number": "602 033 800",
        "trinity_fabric_number": "Z4-3642708",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3642708",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3642708&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42709,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Green Basket Weave",
        "supplier_fabric_number": "602 178 800",
        "trinity_fabric_number": "Z4-3642709",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3642709",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3642709&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42710,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lt Blue Basket Weave",
        "supplier_fabric_number": "602 286 800",
        "trinity_fabric_number": "Z4-3642710",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3642710",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3642710&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42711,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Blue Basket Weave",
        "supplier_fabric_number": "602 028 800",
        "trinity_fabric_number": "Z4-3642711",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3642711",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3642711&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42712,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Royal Blue Basket Weave",
        "supplier_fabric_number": "602 287 800",
        "trinity_fabric_number": "Z4-3642712",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3642712",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3642712&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42713,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Marine Blue Basket Weave",
        "supplier_fabric_number": "602 029 800",
        "trinity_fabric_number": "Z4-3642713",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3642713",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3642713&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42714,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Blue Basket Weave",
        "supplier_fabric_number": "602 288 800",
        "trinity_fabric_number": "Z4-3642714",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3642714",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3642714&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42715,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Black Basket Weave",
        "supplier_fabric_number": "602 027 800",
        "trinity_fabric_number": "Z4-3642715",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3642715",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3642715&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42716,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Blue Sky Micro Checkerboard",
        "supplier_fabric_number": "880012",
        "trinity_fabric_number": "Y6-3642716",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Y6-3642716",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Y6-3642716&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42717,
        "active": true,
        "in_stock": 1,
        "restock_date": "null",
        "description": "Pink Plum Micro Checkerboard",
        "supplier_fabric_number": "880009",
        "trinity_fabric_number": "Y6-3642717",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Y6-3642717",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Y6-3642717&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42718,
        "active": true,
        "in_stock": 1,
        "restock_date": "null",
        "description": "Blue Marine Micro Checkerboard",
        "supplier_fabric_number": "880010",
        "trinity_fabric_number": "Y6-3642718",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Y6-3642718",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Y6-3642718&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42719,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Rust Brown Micro Checkerboard",
        "supplier_fabric_number": "880011",
        "trinity_fabric_number": "Y6-3642719",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Y6-3642719",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Y6-3642719&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42720,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Black Grey Vintage Puppy Tooth",
        "supplier_fabric_number": "880004",
        "trinity_fabric_number": "Y6-3642720",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Y6-3642720",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Y6-3642720&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42721,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Blue Vintage Puppy Tooth",
        "supplier_fabric_number": "880005",
        "trinity_fabric_number": "Y6-3642721",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Y6-3642721",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Y6-3642721&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42722,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Brown Vintage Puppy Tooth",
        "supplier_fabric_number": "880008",
        "trinity_fabric_number": "Y6-3642722",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Y6-3642722",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Y6-3642722&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42723,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Green Vintage Puppy Tooth",
        "supplier_fabric_number": "880013",
        "trinity_fabric_number": "Y6-3642723",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Y6-3642723",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Y6-3642723&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42724,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Berry Vintage Puppy Tooth",
        "supplier_fabric_number": "880007",
        "trinity_fabric_number": "Y6-3642724",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Y6-3642724",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Y6-3642724&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42725,
        "active": true,
        "in_stock": 1,
        "restock_date": "null",
        "description": "Sky Blue Vintage Puppy Tooth",
        "supplier_fabric_number": "880006",
        "trinity_fabric_number": "Y6-3642725",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Y6-3642725",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Y6-3642725&res=300",
        "inventory_status": "In Stock"
    }
]
```

Returns an array of fabrics.

Use this API call to lookup a fabric by trinity fabric number or supplier fabric number. We recommend using the **fabric_number** parameter to do a lookup, then pulling the first result from the array.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/fabrics`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
collection_id | N/A | Only return fabrics from a specific collection
q | N/A | Wildcard matching search by trinity fabric number, supplier fabric number, and fabric description
fabric_number | N/A | Show fabrics that match a supplier fabric number or a trinity fabric number. The trinity fabric number is an exact match, whereas the supplier number is a wildcard match
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
    "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3339001",
    "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3339001&res=300",
    "inventory_status": "Temp Out",
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