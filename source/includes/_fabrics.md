# Fabrics API

## Fabric Resources

The Trinity Fabrics API provides detailed information on fabrics and collections.  Collections are groups of fabrics.  Here is a detailed list of attributes in those resources:

### Fabric

```json
# Standard Object - Used in a resource collection
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
}
```

Standard Attributes

| Attribute                                       | Description                                                                                                                                                                                                                  |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id <br> <span>integer</span>                    | Unique identifier for the object                                                                                                                                                                                             |
| active <br> <span>boolean</span>                | A fabric can be either active or inactive.  Inactive fabrics are discontinued an will not appear in search results.  *Note: Historical orders made with a discontinued order will still show information about that fabric.* |
| in_stock <br> <span>integer</span>              | A lookup value for fabric status.  `0 = Out of Stock` / Sold Out and not reordered, `1 = In Stock`, `2 = Temp Out` / Temporarily Out of Stock / Fabric is being reordered.                                                   |
| restock_date <br> <span>date</span>             | The date a temporarily out of stock fabric will be restocked and available for orders.  Most of the time this field is empty.                                                                                                |
| description <br> <span>string</span>            | A description of the fabric - E.g., Blue Herringbone                                                                                                                                                                         |
| supplier_fabric_number <br> <span>string</span> | A unique identifier / SKU according to the fabric supplier                                                                                                                                                                   |
| trinity_fabric_number <br> <span>string</span>  | A unique identifier / SKU according to Trinity                                                                                                                                                                               |
| url <br> <span>string</span>                    | The url for a repeatable image of the fabric                                                                                                                                                                                 |
| swatch_url <br> <span>string</span>             | The url for a swatch image of the fabric. This image contains serrated edges. Users can configure the zoom of the image by changing the `res=` parameter in the url to a different number.                                   |
| inventory_status <br> <span>string</span>       | A human readable version of the in_stock attribute                                                                                                                                                                           |

```json
# Extended Object
{
    "id": 40985,
    "active": true,
    "in_stock": 1,
    "restock_date": null,
    "description": "Lavender Dobby",
    "supplier_fabric_number": "P39315/02",
    "trinity_fabric_number": "S2-3540985",
    "url": "https://s7d4.scene7.com/is/image/trinityapparel/S2-3540985",
    "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=S2-3540985&res=300",
    "inventory_status": "In Stock",
    "country_origin": "International",
    "fabric_weight_grams_meter": 125,
    "fabric_grouping": "shirts",
    "pattern": "solid",
    "last_stock_edit_date": "2018-01-19T18:36:51.000Z",
    "collection": ...,
    "composition": ...,
    "mill": ...
}
```

Extended attributes

| Attribute                                           | Description                                                        |
| --------------------------------------------------- | ------------------------------------------------------------------ |
| country_origin <br> <span>string</span>             | Where the fabric was milled                                        |
| fabric_weight_grams_meter <br> <span>integer</span> | Weight in grams per square meter                                   |
| fabric_grouping <br> <span>string</span>            | Fabrics are typically grouped by dominant color                    |
| pattern <br> <span>string</span>                    | Type of pattern. Common values are `stripe`, `check`, and `solid`. |
| last_stock_edit_date <br> <span>datetime</span>     | The last time the fabric inventory level was changed               |
| fabric_year <br> <span>year</span>                  | The year the fabric was released                                   |
| collection <br> <span>subresource</span>            | The collection in which the fabric was released                    |
| composition <br> <span>subresource</span>           | The material composition of the fabric (E.g, 100% Wool)            |
| mill <br> <span>subresource</span>                  | The mill that produced the fabric                                  |

### Collection

```json
# Standard Object - Used in a resource collection
{
    "id": 1309,
    "name": "Derby Performance Cornerstone Suitings V17011"
}
```

Standard Attributes

| Attribute                     | Description                      |
| ----------------------------- | -------------------------------- |
| id <br> <span>integer</span>  | Unique identifier for the object |
| name <br> <span>string</span> | The title of the collection      |

```json
# Extended Object
```json
{
    "id": 1854,
    "name": "Outerwear V18082",
    "description": "",
    "fabrics": [...]
}
```

Extended attributes (in addition to standard attributes)

| Attribute                             | Description                                                                                    |
| ------------------------------------- | ---------------------------------------------------------------------------------------------- |
| description <br> <span>string</span>  | A one to two paragraph descripton of the collection                                            |
| fabrics <br> <span>subresource</span> | A list of all fabrics that are a part of the collection. *NOTE: Inactive fabrics may be shown* |

### Composition

```json
# Standard Object - Used in a resource collection
{
    "id": 13,
    "description": "100% Cotton"
}
```

Standard Attributes

| Attribute                            | Description                                   |
| ------------------------------------ | --------------------------------------------- |
| id <br> <span>string</span>          | Unique identifier for the object              |
| description <br> <span>string</span> | A brief description of the fabric composition |

### Mill

```json
# Standard Object - Used in a resource collection
{
    "id": 1049,
    "name": "Soktas"
}
```

Standard Attributes

| Attribute                     | Description                      |
| ----------------------------- | -------------------------------- |
| id <br> <span>integer</span>  | Unique identifier for the object |
| name <br> <span>string</span> | The name of the mill             |


## Get All Collections

```shell
curl "https://api.trinity-apparel.com/v1/collections"
  -H "Authorization Bearer: swaledale"
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

| Parameter | Default | Description                                                                                                       |
| --------- | ------- | ----------------------------------------------------------------------------------------------------------------- |
| is_active | true    | If set to true, the result will only include active fabrics                                                       |
| extended  | false   | If set to true, the API call returns extended objects which include a complete set of attributes and subresources |

### Other

- Permissions: All
- Pagination: Yes

## Get a Specific Collection

```shell
curl "https://api.trinity-apparel.com/v1/collections/1854"
  -H "Authorization Bearer: swaledale"
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
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/C4-3754875",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754875&res=300",
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
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/C4-3754876",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754876&res=300",
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
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/C4-3754877",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754877&res=300",
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
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/C4-3754878",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754878&res=300",
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
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/C4-3754879",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754879&res=300",
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
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/C4-3754880",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754880&res=300",
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
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/C4-3754881",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754881&res=300",
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
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/C4-3754882",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754882&res=300",
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
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z6-3754883",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z6-3754883&res=300",
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
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z6-3754884",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z6-3754884&res=300",
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
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z6-3754885",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z6-3754885&res=300",
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
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3754886",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3754886&res=300",
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
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z6-3754887",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z6-3754887&res=300",
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
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z6-3754888",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z6-3754888&res=300",
            "inventory_status": "In Stock"
        }
    ]
}
```

Returns details on a fabric collection and a list of all fabrics in that collection.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/collections/:id`

### Query Parameters

| Parameter | Default | Description                                |
| --------- | ------- | ------------------------------------------ |
| id        | N/A     | The specific collection id you want to see |

### Other

- Permissions: All
- Pagination: N/A

## Get All Fabrics

```shell
curl "https://api.trinity-apparel.com/v1/fabrics"
  -H "Authorization Bearer: swaledale"
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

| Parameter              | Default | Description                                                                                                                                                               |
| ---------------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| collection_id          | N/A     | Only return fabrics from a specific collection                                                                                                                            |
| q                      | N/A     | Wildcard matching search by trinity fabric number, supplier fabric number, and fabric description                                                                         |
| fabric_number          | N/A     | Show fabrics that match a supplier fabric number or a trinity fabric number. The trinity fabric number is an exact match, whereas the supplier number is a wildcard match |
| trinity_fabric_number  | N/A     | Show fabrics that match a specific Trinity fabric number.  *See below for example querying for multiple fabrics.*                                                         |
| supplier_fabric_number | N/A     | Show fabrics that match a specific Supplier fabric number.  *See below for example querying for multiple fabrics.*                                                        |
| is_active              | true    | If set to true, the result will only include active fabrics                                                                                                               |
| show_archived          | false   | By default archived fabrics (not active, not in stock or temp out) are not returned.  Set this to true in order to show all fabrics.                                      |
| reverse_sort           | N/A     | If this parameter is sort, fabrics will be sorted descending by fabric_id                                                                                                 |
| extended               | false   | If set to true, the API call returns extended objects which include a complete set of attributes and subresources                                                         |

### Other

- Permissions: All
- Pagination: Yes

### Querying by multiple fabric numbers

In order to query for multiple fabric numbers, you will pass in multiple params with the format like below:

`GET https://api.trinity-apparel.com/v1//fabrics?trinity_fabric_number[]=C4-3754922&trinity_fabric_number[]=C4-3754923&trinity_fabric_number[]=C4-3754924`

OR

`GET https://api.trinity-apparel.com/v1//fabrics?supplier_fabric_number[]=602%20275%20800&supplier_fabric_number[]=602%20275%20802&supplier_fabric_number[]=602%20275%20802`

## Get a Specific Fabric

```shell
curl "https://api.trinity-apparel.com/v1/fabrics/40985"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
    "id": 40985,
    "active": true,
    "in_stock": 1,
    "restock_date": null,
    "description": "Lavender Dobby",
    "supplier_fabric_number": "P39315/02",
    "trinity_fabric_number": "S2-3540985",
    "url": "https://s7d4.scene7.com/is/image/trinityapparel/S2-3540985",
    "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=S2-3540985&res=300",
    "inventory_status": "In Stock",
    "country_origin": "International",
    "fabric_weight_grams_meter": 125,
    "fabric_grouping": "shirts",
    "pattern": "solid",
    "last_stock_edit_date": "2018-01-19T18:36:51.000Z",
    "fabric_year": 2017,
    "collection": {
        "id": 1520,
        "name": "Soktas Bespoke V17082"
    },
    "composition": {
        "id": 13,
        "description": "100% Cotton"
    },
    "mill": {
        "id": 1049,
        "name": "Soktas"
    }
}
```

Returns details on a specific fabric.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/fabrics/:id`

### Query Parameters

| Parameter | Default | Description                            |
| --------- | ------- | -------------------------------------- |
| id        | N/A     | The specific fabric id you want to see |

### Other

- Permissions: All
- Pagination: N/A

## Get Related Fabrics

```shell
curl "https://api.trinity-apparel.com/v1/fabrics/39001/related"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 39000,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Linen Blue Dot",
        "supplier_fabric_number": "55699-16",
        "trinity_fabric_number": "Z8-3339000",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3339000",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3339000&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38992,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lt Blue Solid",
        "supplier_fabric_number": "FL51168-13",
        "trinity_fabric_number": "Z8-3338992",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338992",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338992&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38993,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lt Blue Gingham",
        "supplier_fabric_number": "FL60629-13",
        "trinity_fabric_number": "Z8-3338993",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338993",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338993&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38994,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Med Blue Gingham",
        "supplier_fabric_number": "FL60629-15",
        "trinity_fabric_number": "Z8-3338994",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338994",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338994&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38979,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lt Blue Hairline Stripe",
        "supplier_fabric_number": "FL54667-13",
        "trinity_fabric_number": "Z8-3338979",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338979",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338979&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38984,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Teal Hairline Stripe",
        "supplier_fabric_number": "FL54667-11",
        "trinity_fabric_number": "Z8-3338984",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338984",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338984&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38985,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lt Blue Mini Check",
        "supplier_fabric_number": "FL63933-13",
        "trinity_fabric_number": "Z8-3338985",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338985",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338985&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38991,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "White Solid",
        "supplier_fabric_number": "FL51168-1",
        "trinity_fabric_number": "Z8-3338991",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338991",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338991&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38980,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Purple Hairline Stripe",
        "supplier_fabric_number": "FL54667-15",
        "trinity_fabric_number": "Z8-3338980",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338980",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338980&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38981,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Pink Hairline Stripe",
        "supplier_fabric_number": "FL54667-31",
        "trinity_fabric_number": "Z8-3338981",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338981",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338981&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38982,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Raspberry Hairline Stripe",
        "supplier_fabric_number": "FL54667-83",
        "trinity_fabric_number": "Z8-3338982",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338982",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338982&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38983,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lime Hairline Stripe",
        "supplier_fabric_number": "FL54667-53",
        "trinity_fabric_number": "Z8-3338983",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338983",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338983&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38986,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Purple Mini Check",
        "supplier_fabric_number": "FL63933-15",
        "trinity_fabric_number": "Z8-3338986",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338986",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338986&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38987,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Pink Mini Check",
        "supplier_fabric_number": "FL63933-31",
        "trinity_fabric_number": "Z8-3338987",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338987",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338987&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38988,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Raspberry Mini Check",
        "supplier_fabric_number": "FL63933-83",
        "trinity_fabric_number": "Z8-3338988",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338988",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338988&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38989,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lime Mini Check",
        "supplier_fabric_number": "FL63933-53",
        "trinity_fabric_number": "Z8-3338989",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338989",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338989&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38990,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Teal Mini Check",
        "supplier_fabric_number": "FL63933-11",
        "trinity_fabric_number": "Z8-3338990",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338990",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338990&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 38997,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Demim",
        "supplier_fabric_number": "FM300583-100",
        "trinity_fabric_number": "Z8-3338997",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338997",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338997&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 39002,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lt Blue Mini Check w/ Dot",
        "supplier_fabric_number": "FL66290-11",
        "trinity_fabric_number": "Z4-3339002",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3339002",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3339002&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 33056,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "White Poplin",
        "supplier_fabric_number": "FM39497-1",
        "trinity_fabric_number": "Z8-3333056",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3333056",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3333056&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 33058,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lt Blue End on End",
        "supplier_fabric_number": "FM37748-12",
        "trinity_fabric_number": "Z8-3333058",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3333058",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3333058&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 33059,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Blue End on End",
        "supplier_fabric_number": "FM37748-13",
        "trinity_fabric_number": "Z8-3333059",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3333059",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3333059&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 33069,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lt Blue Micro Stripe",
        "supplier_fabric_number": "FM39477-113",
        "trinity_fabric_number": "Z8-3333069",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3333069",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3333069&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 33070,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Blue Micro Stripe",
        "supplier_fabric_number": "FM39477-15",
        "trinity_fabric_number": "Z8-3333070",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3333070",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3333070&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 33074,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Violet Graph Check",
        "supplier_fabric_number": "FM25979-85",
        "trinity_fabric_number": "Z8-3333074",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3333074",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3333074&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 33075,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Red Graph Check",
        "supplier_fabric_number": "FM25979-35",
        "trinity_fabric_number": "Z8-3333075",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3333075",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3333075&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 33083,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lt Bue Gingham",
        "supplier_fabric_number": "FM16617-13",
        "trinity_fabric_number": "Z8-3333083",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3333083",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3333083&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 33084,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Gingham",
        "supplier_fabric_number": "FM16617-19",
        "trinity_fabric_number": "Z8-3333084",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3333084",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3333084&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 33092,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lt Blue Stripe",
        "supplier_fabric_number": "FM37751-13",
        "trinity_fabric_number": "Z8-3333092",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3333092",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3333092&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 33093,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Blue Stripe",
        "supplier_fabric_number": "FM37751-15",
        "trinity_fabric_number": "Z8-3333093",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3333093",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3333093&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 33094,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Violet Stripe",
        "supplier_fabric_number": "FM37751-86",
        "trinity_fabric_number": "Z8-3333094",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3333094",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3333094&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 33095,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Fuchsia Stripe",
        "supplier_fabric_number": "FM37751-85",
        "trinity_fabric_number": "Z8-3333095",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3333095",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3333095&res=300",
        "inventory_status": "In Stock"
    }
]
```

Returns a list of related fabrics

### HTTP Request

`GET https://api.trinity-apparel.com/v1/fabrics/:id/related`

### Query Parameters

| Parameter | Default | Description                                                |
| --------- | ------- | ---------------------------------------------------------- |
| id        | N/A     | The specific fabric id you want to see related fabrics for |

### Other

- Permissions: All
- Pagination: N/A - Limited to 32 results