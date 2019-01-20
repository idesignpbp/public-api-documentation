# Fabrics API

## Resources

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

Attribute | Type | Description
---------- | ------- | -------
id | string | Unique identifier for the object
active | boolean | A fabric can be either active or inactive.  Inactive fabrics are discontinued an will not appear in search results.  *Note: Historical orders made with a discontinued order will still show information about that fabric.*
in_stock | integer | A lookup value for fabric status.  `0 = Out of Stock` / Sold Out and not reordered, `1 = In Stock`, `2 = Temp Out` / Temporarily Out of Stock / Fabric is being reordered.
restock_date | date | The date a temporarily out of stock fabric will be restocked and available for orders.  Most of the time this field is empty.
description | string | A description of the fabric - E.g., Blue Herringbone
supplier_fabric_number | string | A unique identifier / SKU according to the fabric supplier
trinity_fabric_number | string | A unique identifier / SKU according to Trinity
url | string | The url for a repeatable image of the fabric
swatch_url | string | The url for a swatch image of the fabric. This image contains serrated edges. Users can also configure the zoom of the image by changing the `res=` parameter in the url to a different number.
inventory_status | string | a human readable version of the in_stock attribute

```json
# Expanded Object
{
    "id": 39001,
    "active": true,
    "supplier_fabric_num": "54557-18",
    "trinity_fabric_num": "Z8-3339001",
    "country_origin": "Italy",
    "fabric_weight_grams_meter": 105,
    "fabric_grouping": "blue",
    "pattern": "Foulards/Neats",
    "in_stock": 2,
    "restock_date": null,
    "last_stock_edit_date": "2017-02-27T16:43:46.000Z",
    "fabric_year": 2016,
    "created_at": "2017-02-27T16:43:46.000Z",
    "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3339001",
    "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3339001&res=300",
    "inventory_status": "Temp Out",
    "collection": ...
}
```

Expanded attributes (in addition to standard attributes)

Attribute | Type | Description
---------- | ------- | -------
country_origin | string | Where the fabric was milled
fabric_weight_grams_meter | integer | weight in grams / square meter
fabric_grouping | string | Fabrics are typically grouped by dominant color
pattern | string | Type of pattern. Common values are stripe, check, and solid.
last_stock_edit_date  | datetime | The last time the fabric inventory level was changed
collection | subresource | The collection is embedded within the fabric resource

### Collection

```json
# Standard Object - Used in a resource collection
{
    "id": 1309,
    "name": "Derby Performance Cornerstone Suitings V17011"
}
```

Standard Attributes

Attribute | Type | Description
---------- | ------- | -------
id | string | Unique identifier for the object
name | string | The title of the collection

```json
# Expanded Object
{
    "id": 1309,
    "name": "Derby Performance Cornerstone Suitings V17011",
    "description": "",
    "fabrics": ...
}
```

Expanded attributes (in addition to standard attributes)

Attribute | Type | Description
---------- | ------- | -------
description | string | A one to two paragraph descripton of the collection
fabrics | subresource | a list of all fabrics that are a part of the collection. *NOTE: Inactive fabrics may be shown*


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
show_archived | false | By default archived fabrics (not active, not in stock or temp out) are not returned.  Set this to true in order to show all fabrics.
reverse_sort | N/A | If this parameter is sort, fabrics will be sorted descending by fabric_id

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

## Get Related Fabrics

```shell
curl "https://api.trinity-apparel.com/v1/fabrics/39001/related"
  -H "AUTHENTICATION Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 36467,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Windowpane",
        "supplier_fabric_number": "2258 18 540",
        "trinity_fabric_number": "Z3-3536467",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3536467",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3536467&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 44970,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Windowpane",
        "supplier_fabric_number": "2261 28 660",
        "trinity_fabric_number": "Z3-3744970",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3744970",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3744970&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 45315,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Windowpane",
        "supplier_fabric_number": "801 719 760",
        "trinity_fabric_number": "Z3-3745315",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3745315",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3745315&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 45460,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Windowpane",
        "supplier_fabric_number": "26712-195",
        "trinity_fabric_number": "K5-3745460",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/K5-3745460",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=K5-3745460&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 45355,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Windowpane",
        "supplier_fabric_number": "108184",
        "trinity_fabric_number": "K1-3745355",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/K1-3745355",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=K1-3745355&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 40837,
        "active": true,
        "in_stock": 1,
        "restock_date": "null",
        "description": "Navy Windowpane",
        "supplier_fabric_number": "835022",
        "trinity_fabric_number": "Y4-3540837",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Y4-3540837",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Y4-3540837&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 47366,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "NAVY WINDOWPANE",
        "supplier_fabric_number": "510277",
        "trinity_fabric_number": "XB-3747366",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/XB-3747366",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=XB-3747366&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 47607,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "NAVY WINDOWPANE",
        "supplier_fabric_number": "510058",
        "trinity_fabric_number": "XC-3747607",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/XC-3747607",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=XC-3747607&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 56761,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Windowpane",
        "supplier_fabric_number": "CM0161NVY",
        "trinity_fabric_number": "TR-3756761",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/TR-3756761",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=TR-3756761&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 53161,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Windowpane",
        "supplier_fabric_number": "CH0134RYB",
        "trinity_fabric_number": "N4-3753161",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/N4-3753161",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N4-3753161&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 32278,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Windowpane",
        "supplier_fabric_number": "2251 11 660",
        "trinity_fabric_number": "Z3-3332278",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3332278",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3332278&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 56480,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Windowpane",
        "supplier_fabric_number": "#34C Navy",
        "trinity_fabric_number": "TR-3756480",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/TR-3756480",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=TR-3756480&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 53434,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Windowpane",
        "supplier_fabric_number": "CM0161NVY",
        "trinity_fabric_number": "N1-3653434",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/N1-3653434",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N1-3653434&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 53153,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Windowpane",
        "supplier_fabric_number": "#34C Navy",
        "trinity_fabric_number": "N4-3753153",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/N4-3753153",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N4-3753153&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 26402,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Windowpane",
        "supplier_fabric_number": "2238 15 540",
        "trinity_fabric_number": "K3-3026402",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/K3-3026402",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=K3-3026402&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 44979,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy bold Check",
        "supplier_fabric_number": "2261 30 660",
        "trinity_fabric_number": "Z3-3744979",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3744979",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3744979&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 45006,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Royal Blue Micro Check",
        "supplier_fabric_number": "2261 51 660",
        "trinity_fabric_number": "Z3-3745006",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3745006",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3745006&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 45007,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Micro Check",
        "supplier_fabric_number": "2261 52 660",
        "trinity_fabric_number": "Z3-3745007",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3745007",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3745007&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 41121,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Windowpane",
        "supplier_fabric_number": "YGC-185-B",
        "trinity_fabric_number": "A4-3541121",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/A4-3541121",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=A4-3541121&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 36463,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Admiral Blue Bold Check",
        "supplier_fabric_number": "2258 14 540",
        "trinity_fabric_number": "Z3-3536463",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3536463",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3536463&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 36470,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lt Blue Mini Houndstooth",
        "supplier_fabric_number": "2258 06 540",
        "trinity_fabric_number": "Z3-3536470",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3536470",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3536470&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 36477,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Fancy Check",
        "supplier_fabric_number": "2258 16 540",
        "trinity_fabric_number": "Z3-3536477",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3536477",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3536477&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 36469,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Mini Check",
        "supplier_fabric_number": "2258 67 540",
        "trinity_fabric_number": "Z3-3536469",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3536469",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3536469&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 36481,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Tic Check",
        "supplier_fabric_number": "2258 69 540",
        "trinity_fabric_number": "Z3-3536481",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3536481",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3536481&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 36483,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Lt Blue Beaded Windowpane",
        "supplier_fabric_number": "2258 65 540",
        "trinity_fabric_number": "Z3-3536483",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3536483",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3536483&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 40264,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Windowpane",
        "supplier_fabric_number": "183490/6",
        "trinity_fabric_number": "Z2-3340264",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z2-3340264",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z2-3340264&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42316,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Blue Lt Blue Windowpane",
        "supplier_fabric_number": "8016 11 700",
        "trinity_fabric_number": "Z3-3642316",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3642316",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3642316&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42324,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Blue Muted Check",
        "supplier_fabric_number": "8016 20 700",
        "trinity_fabric_number": "Z3-3642324",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3642324",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3642324&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42327,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Mini Check",
        "supplier_fabric_number": "8016 23 700",
        "trinity_fabric_number": "Z3-3642327",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3642327",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3642327&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 42347,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Self Check",
        "supplier_fabric_number": "8016 17 700",
        "trinity_fabric_number": "Z3-3642347",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3642347",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3642347&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 45080,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Blue Windowpane",
        "supplier_fabric_number": "6019 12 600",
        "trinity_fabric_number": "Z3-3745080",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3745080",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3745080&res=300",
        "inventory_status": "In Stock"
    },
    {
        "id": 36498,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Navy Hairline Windowpane",
        "supplier_fabric_number": "6004 78 520",
        "trinity_fabric_number": "Z3-3536498",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z3-3536498",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z3-3536498&res=300",
        "inventory_status": "In Stock"
    }
]
```

Returns a list of related fabrics

### HTTP Request

`GET https://api.trinity-apparel.com/v1/fabrics/:id/related`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
id | N/A | The specific fabric id you want to see related fabrics for

### Other

- Permissions: All
- Pagination: N/A - Limited to 32 results