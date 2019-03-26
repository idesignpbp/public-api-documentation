# Fabrics API

## Fabric Resources

The Trinity Fabrics API provides detailed information on fabrics and collections.  Collections are groups of fabrics.  Here is a detailed list of attributes in those resources:

### Fabric

```json
# Standard Object - Used in a resource collection
{
    "id": 61189,
    "active": true,
    "in_stock": 1,
    "restock_date": null,
    "description": "Black solid",
    "supplier_fabric_number": "53145",
    "trinity_fabric_number": "XG-3861189",
    "url": "https://s7d4.scene7.com/is/image/trinityapparel/XG-3861189",
    "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=XG-3861189&res=300",
    "inventory_status": "In Stock",
    "price_tier": 4,
    "has_image": true
}
{
    "id": 61189,
    "active": true,
    "in_stock": 1,
    "restock_date": null,
    "description": "Black solid",
    "supplier_fabric_number": "53145",
    "trinity_fabric_number": "XG-3861189",
    "url": "https://s7d4.scene7.com/is/image/trinityapparel/XG-3861189",
    "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=XG-3861189&res=300",
    "inventory_status": "In Stock",
    "pattern_id": 1,
    "weave_id": null,
    "price_tier": 4,
    "has_image": false
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
| pattern_id <br> <span>integer</span>            | The unique ID for the pattern of the fabric.                                                                                                                                                                                 |
| weave_id <br> <span>integer</span>              | The unique ID for the weave of the fabric.                                                                                                                                                                                   |
| price_tier <br> <span>integer</span>            | If set, will be a ranking between 1-4 of how expensive the fabric is (1 being least expensive, 4 being most expensive).                                                                                                      |
| has_image <br> <span>boolean</span>             | If true, the fabric image url will actually return an image of the fabric.                                                                                                                                                   |

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
    "pattern_id": null,
    "weave_id": 3,
    "price_tier": 3,
    "has_image": false,
    "country_origin": "International",
    "fabric_grouping": "shirts",
    "pattern": null,
    "usage": "Garments",
    "last_stock_edit_date": "2018-01-19T18:36:51.000Z",
    "fabric_year": 2017,
    "fabric_garment_types": ...,
    "trim_garment_types": ...,
    "weight": 125,
    "lead_time": "Stocked",
    "alternate_images": ...,
    "collection": ...,
    "weave": ...,
    "price_code": ...,
    "supplier": ...,
    "composition": ...
}
```

Extended attributes

| Attribute                                          | Description                                                           |
| -------------------------------------------------- | --------------------------------------------------------------------- |
| country_origin <br> <span>string</span>            | Where the fabric was milled.                                          |
| fabric_grouping <br> <span>string</span>           | Fabrics are typically grouped by dominant color.                      |
| pattern <br> <span>string</span>                   | Type of pattern. Common values are `stripe`, `check`, and `solid`.    |
| usage <br> <span>integer</span>                    | The usage of the fabric (E.g., Shirt Trim, Clothing Trim, etc).       |
| last_stock_edit_date <br> <span>datetime</span>    | The last time the fabric inventory level was changed.                 |
| fabric_year <br> <span>year</span>                 | The year the fabric was released.                                     |
| fabric_garment_types <br> <span>subresource</span> | An array of the garment types a fabric is used for.                   |
| trim_garment_types <br> <span>subresource</span>   | An array of the garment types a trim is used for.                     |
| weight <br> <span>integer</span>                   | Weight in grams per square meter.                                     |
| lead_time <br> <span>string</span>                 | If the fabric is in stock or the estimated time until it is in stock. |
| alternate_images <br> <span>subresource</span>     | An array of alternate images for a fabric.                            |
| collection <br> <span>subresource</span>           | The collection in which the fabric was released.                      |
| weave <br> <span>subresource</span>                | Information about the weave of a fabric.                              |
| price_code <br> <span>subresource</span>           | Information about the price code for the fabric.                      |
| supplier <br> <span>subresource</span>             | Information about the supplier of the fabric.                         |
| composition <br> <span>subresource</span>          | The material composition of the fabric (E.g, 100% Wool).              |

### Fabric Garment Types

```json
# Standard Object - Used in a resource collection
[
    "CSC",
    "CV",
    "CT",
    "CSHO",
    "CBK"
]
```

Standard Attributes

| Attribute                | Description                                                             |
| ------------------------ | ----------------------------------------------------------------------- |
| <br> <span>string</span> | An array of strings that lists each garment type a fabric is valid for. |

### Trim Garment Types

```json
# Standard Object - Used in a resource collection
[
    "CSC",
    "CV",
    "CT",
    "CSHO",
    "CBK"
]
```

Standard Attributes

| Attribute                | Description                                                           |
| ------------------------ | --------------------------------------------------------------------- |
| <br> <span>string</span> | An array of strings that lists each garment type a trim is valid for. |

### Alternate Images

```json
# Standard Object - Used in a resource collection
[
    {
        "name": "CSC",
        "description": "Jacket Laydown",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/CSC202-NT-4x4?&obj=CSC/Fabric&src=CMT-70001&res=300&obj=CSC/Buttons&color=43,43,43&obj=CSC/Thread/Thread&color=36,36,36&obj=CSCLining&src=LL-2617432&obj=CSC/Fabric/Lapel&src=CMT-70001&res=300&obj=CSC/Fabric/Collar&src=CMT-70001&res=300&obj=CSC/Fabric/Pockets/Breast_PKT&src=CMT-70001&res=300&obj=CSC/Fabric/Pkt_Cordingsrc=CMT-70001&res=300"
    },
    {
        "name": "CV",
        "description": "Vest Laydown",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/CV2-LINED-2x3?&obj=CV/Fabric&src=CMT-70001&res=300&obj=CV/Buttons&color=37,37,49&obj=CV/Thread&color=28,33,50&obj=CV/Liningsrc=LL-2617432&res=300&wid=200"
    },
    {
        "name": "CT",
        "description": "Trouser Laydown",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/CT-T0-OW-2X3?&obj=CT/Fabric&src=CMT-70001&res=300&obj=CT/Buttons&color=37,37,49&obj=CT/Thread&color=28,33,50&wid=200"
    },
    {
        "name": "CSHT",
        "description": "Shirt Laydown",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/CSHT-AS-FC4AMF-4x4?&obj=CSHT/Fabric&src=CMT-70001&res=300&obj=CSHT/Buttons&color=235,230,214&obj=CSHT/Thread&color=244,241,244obj=CSHT/Fabric/Neckband_In&src=CMT-70001&res=300&obj=CSHT/Fabric/Collar&src=CMT-70001&res=300&obj=CSHT/Fabric/Yoke_In&src=CMT-70001&res=300&obj=CSHT/Fabric/Cuff_Out&src=CMT-70001&res=300obj=CSHT/Fabric/Fronts/Placket&src=CMT-70001&res=300"
    }
]
```

Standard Attributes

| Attribute                            | Description                                          |
| ------------------------------------ | ---------------------------------------------------- |
| name <br> <span>string</span>        | The garment type used in the alternate image.        |
| description <br> <span>string</span> | A human readable description of the alternate image. |
| url <br> <span>integer</span>        | The url for the image itself.                        |

### Weave

```json
# Standard Object - Used in a resource collection
{
    "id": 4,
    "name": "poplin",
    "position": 4
}
```

Standard Attributes

| Attribute                          | Description                       |
| ---------------------------------- | --------------------------------- |
| id <br> <span>integer</span>       | Unique identifier for the object. |
| name <br> <span>string</span>      | The name of the weave.            |
| position <br> <span>integer</span> | The position of the weave.        |

### Price Code

```json
# Standard Object - Used in a resource collection
{
    "code": "S2",
    "description": "Soktas Bespoke",
    "tier": 3
}
```

Standard Attributes

| Attribute                            | Description                                                                                                             |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
| code <br> <span>string</span>        | Unique identifier for the object.                                                                                       |
| description <br> <span>string</span> | A human readable description of the price code.                                                                         |
| tier <br> <span>integer</span>       | If set, will be a ranking between 1-4 of how expensive the fabric is (1 being least expensive, 4 being most expensive). |

### Collection

```json
# Standard Object - Used in a resource collection
{
    "id": 1309,
    "name": "Derby Performance Cornerstone Suitings V17011",
    "title": "Derby Performance Cornerstone Suitings",
    "datecode": "V17011",
    "image": "https://s7d4.scene7.com/is/image/trinityapparel/Derby_Performance_Cornerstone_Suitings_V17011?&hei=100",
    "featured_fabric": ...
}
```

Standard Attributes

| Attribute                                     | Description                                                                                                                                                                                                 |
| --------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id <br> <span>integer</span>                  | Unique identifier for the object                                                                                                                                                                            |
| name <br> <span>string</span>                 | The title of the collection                                                                                                                                                                                 |
| title <br> <span>string</span>                | The name of the collection without the datecode.                                                                                                                                                            |
| datecode <br> <span>string</span>             | The datecode of the collection (E.g., v18011). The first two digits are the year (2018), the next two are the month (01 = January), and the last one is which release we did during that month (1 = first). |
| image <br> <span>string</span>                | URL to a thumbnail image for the collection. Image size is 105x100 px.                                                                                                                                      |
| featured_fabric <br> <span>subresource</span> | The featured fabric is shown in collection previews. It is typically the first fabric in the collection.                                                                                                    |

```json
# Extended Object
```json
{
    "id": 1854,
    "name": "Outerwear V18082",
    "title": "Outerwear",
    "datecode": "V18082",
    "image": "https://s7d4.scene7.com/is/image/trinityapparel/Outerwear_V18082?&hei=100",
    "description": "",
    "featured_fabric": ...,
    "fabrics": [...]
}
```

Extended attributes (in addition to standard attributes)

| Attribute                             | Description                                                                                    |
| ------------------------------------- | ---------------------------------------------------------------------------------------------- |
| description <br> <span>string</span>  | A one to two paragraph descripton of the collection.                                           |
| fabrics <br> <span>subresource</span> | A list of all fabrics that are a part of the collection. *NOTE: Inactive fabrics may be shown* |

### Supplier

```json
# Standard Object - Used in a resource collection
{
    "id": 481,
    "code": "FW",
    "name": "Supplier",
    "city": "Springdale",
    "state": "Arkansas",
    "country": "USA"
}
```

Standard Attributes

| Attribute                        | Description                            |
| -------------------------------- | -------------------------------------- |
| id <br> <span>string</span>      | Unique identifier for the object.      |
| code <br> <span>string</span>    | The abbreviated name for a supplier.   |
| name <br> <span>string</span>    | The name of the supplier.              |
| city <br> <span>string</span>    | The city of the supplier's address.    |
| state <br> <span>string</span>   | The state of the supplier's address.   |
| country <br> <span>string</span> | The country of the supplier's address. |

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
        "name": "Derby Performance Cornerstone Suitings V17011",
        "title": "Derby Performance Cornerstone Suitings",
        "datecode": "V17011",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/Derby_Performance_Cornerstone_Suitings_V17011?&hei=100",
        "featured_fabric": {
            "id": 37087,
            "active": true,
            "in_stock": 1,
            "restock_date": null,
            "description": "Lt Grey Blue Glenplaid",
            "supplier_fabric_number": "59918-2",
            "trinity_fabric_number": "C6-3337087",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/C6-3337087",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C6-3337087&res=300",
            "inventory_status": "In Stock"
        }
    },
    {
        "id": 1312,
        "name": "Sartorial Dress V17011",
        "title": "Sartorial Dress",
        "datecode": "V17011",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/Sartorial_Dress_V17011?&hei=100",
        "featured_fabric": {
            "id": 36835,
            "active": true,
            "in_stock": 1,
            "restock_date": null,
            "description": "Oxford Gray Solid",
            "supplier_fabric_number": "107707",
            "trinity_fabric_number": "C6-3336835",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/C6-3336835",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C6-3336835&res=300",
            "inventory_status": "In Stock"
        }
    },
    {
        "id": 1317,
        "name": "Derby Performance Contemporary Suitings V17011",
        "title": "Derby Performance Contemporary Suitings",
        "datecode": "V17011",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/Derby_Performance_Contemporary_Suitings_V17011?&hei=100",
        "featured_fabric": {
            "id": 37022,
            "active": true,
            "in_stock": 1,
            "restock_date": null,
            "description": "Grey Pink Plaid",
            "supplier_fabric_number": "59905-1",
            "trinity_fabric_number": "C6-3337022",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/C6-3337022",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C6-3337022&res=300",
            "inventory_status": "In Stock"
        }
    },
    {
        "id": 1318,
        "name": "Kensington Brighton Sport Coats V17011",
        "title": "Kensington Brighton Sport Coats",
        "datecode": "V17011",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/Kensington_Brighton_Sport_Coats_V17011?&hei=100",
        "featured_fabric": {
            "id": 36961,
            "active": true,
            "in_stock": 1,
            "restock_date": null,
            "description": "Blue Red Windowpane",
            "supplier_fabric_number": "25002-2",
            "trinity_fabric_number": "K4-3336961",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/K4-3336961",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=K4-3336961&res=300",
            "inventory_status": "In Stock"
        }
    },
    {
        "id": 1319,
        "name": "Dormeuil Iconik Nano 704 V17011",
        "title": "Dormeuil Iconik Nano 704",
        "datecode": "V17011",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/Dormeuil_Iconik_Nano_704_V17011?&hei=100",
        "featured_fabric": {
            "id": 37152,
            "active": true,
            "in_stock": 0,
            "restock_date": "null",
            "description": "Grey Rope Stripe",
            "supplier_fabric_number": "264001",
            "trinity_fabric_number": "Y4-3437152",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/Y4-3437152",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Y4-3437152&res=300",
            "inventory_status": "Sold Out"
        }
    },
    {
        "id": 1320,
        "name": "Dormeuil Amadeus Jacketings 365 No.702 V17011",
        "title": "Dormeuil Amadeus Jacketings 365 No.702",
        "datecode": "V17011",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/Dormeuil_Amadeus_Jacketings_365_No.702_V17011?&hei=100",
        "featured_fabric": {
            "id": 37217,
            "active": true,
            "in_stock": 1,
            "restock_date": null,
            "description": "Burgundy Plaid",
            "supplier_fabric_number": "420083",
            "trinity_fabric_number": "Y4-3437217",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/Y4-3437217",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Y4-3437217&res=300",
            "inventory_status": "In Stock"
        }
    },
    {
        "id": 1321,
        "name": "Sartorial Volume 1 V17011",
        "title": "Sartorial Volume 1",
        "datecode": "V17011",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/Sartorial_Volume_1_V17011?&hei=100",
        "featured_fabric": {
            "id": 37261,
            "active": true,
            "in_stock": 1,
            "restock_date": null,
            "description": "White Solid",
            "supplier_fabric_number": "65167",
            "trinity_fabric_number": "C4-3337261",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/C4-3337261",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3337261&res=300",
            "inventory_status": "In Stock"
        }
    },
    {
        "id": 1322,
        "name": "Derby Performance Corinthian Sport Coats V17011",
        "title": "Derby Performance Corinthian Sport Coats",
        "datecode": "V17011",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/Derby_Performance_Corinthian_Sport_Coats_V17011?&hei=100",
        "featured_fabric": {
            "id": 37619,
            "active": true,
            "in_stock": 1,
            "restock_date": null,
            "description": "Lavender Grey Black Check",
            "supplier_fabric_number": "59510-2",
            "trinity_fabric_number": "C6-3337619",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/C6-3337619",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C6-3337619&res=300",
            "inventory_status": "In Stock"
        }
    },
    {
        "id": 1323,
        "name": "Zenith Riviera V17011",
        "title": "Zenith Riviera",
        "datecode": "V17011",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/Zenith_Riviera_V17011?&hei=100",
        "featured_fabric": {
            "id": 37725,
            "active": true,
            "in_stock": 1,
            "restock_date": null,
            "description": "Blue  Lt Blue Check",
            "supplier_fabric_number": "609 042 900",
            "trinity_fabric_number": "Z4-3337725",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3337725",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3337725&res=300",
            "inventory_status": "In Stock"
        }
    },
    {
        "id": 1324,
        "name": "Norwich TravelEase V17011",
        "title": "Norwich TravelEase",
        "datecode": "V17011",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/Norwich_TravelEase_V17011?&hei=100",
        "featured_fabric": {
            "id": 37790,
            "active": true,
            "in_stock": 1,
            "restock_date": null,
            "description": "Charles Herringbone White",
            "supplier_fabric_number": "D#3-C/#11",
            "trinity_fabric_number": "N3-3337790",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/N3-3337790",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N3-3337790&res=300",
            "inventory_status": "In Stock"
        }
    },
    {
        "id": 1325,
        "name": "Dormeuil 703 D Philosphy V17011V",
        "title": "Dormeuil 703 D Philosphy V",
        "datecode": "V17011",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/Dormeuil_703_D_Philosphy_V17011V?&hei=100",
        "featured_fabric": {
            "id": 37828,
            "active": true,
            "in_stock": 0,
            "restock_date": "null",
            "description": "Green  Blue Check",
            "supplier_fabric_number": "412001",
            "trinity_fabric_number": "Y4-3437828",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/Y4-3437828",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Y4-3437828&res=300",
            "inventory_status": "Sold Out"
        }
    },
]
```

Returns an array of fabric collections.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/collections`

### Query Parameters

| Parameter    | Default | Description                                                                                                        |
| ------------ | ------- | ------------------------------------------------------------------------------------------------------------------ |
| is_active    | true    | If set to true, the result will only include active collections.                                                   |
| reverse_sort | false   | If set to true, collections will be sorted descending by collection_id.                                            |
| extended     | false   | If set to true, the API call returns extended objects which include a complete set of attributes and subresources. |

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
    "title": "Outerwear",
    "datecode": "V18082",
    "image": "https://s7d4.scene7.com/is/image/trinityapparel/Outerwear_V18082?&hei=100",
    "description": "",
    "featured_fabric": {
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
        "id": 53401,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Blue Broadcloth Stripe",
        "supplier_fabric_number": "1415570-6",
        "trinity_fabric_number": "N1-3653401",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/N1-3653401",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N1-3653401&res=300",
        "inventory_status": "In Stock",
        "pattern_id": 2,
        "weave_id": 5,
        "price_tier": 1,
        "has_image": true
    },
    {
        "id": 53402,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Violet Broadcloth Stripe",
        "supplier_fabric_number": "1415570-7",
        "trinity_fabric_number": "N1-3653402",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/N1-3653402",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N1-3653402&res=300",
        "inventory_status": "In Stock",
        "pattern_id": 2,
        "weave_id": 5,
        "price_tier": 1,
        "has_image": true
    },
    {
        "id": 53403,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Pink Broadcloth Stripe",
        "supplier_fabric_number": "1415570-1",
        "trinity_fabric_number": "N1-3653403",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/N1-3653403",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N1-3653403&res=300",
        "inventory_status": "In Stock",
        "pattern_id": 2,
        "weave_id": 5,
        "price_tier": 1,
        "has_image": true
    },
    {
        "id": 53404,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Grey Broadcloth Stripe",
        "supplier_fabric_number": "1415570-3",
        "trinity_fabric_number": "N1-3653404",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/N1-3653404",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N1-3653404&res=300",
        "inventory_status": "In Stock",
        "pattern_id": 2,
        "weave_id": 5,
        "price_tier": 1,
        "has_image": true
    },
    {
        "id": 53405,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lt Blue Broadcloth Graph Check",
        "supplier_fabric_number": "CM0022LBU",
        "trinity_fabric_number": "N1-3653405",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/N1-3653405",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N1-3653405&res=300",
        "inventory_status": "In Stock",
        "pattern_id": 20,
        "weave_id": 5,
        "price_tier": 1,
        "has_image": true
    },
    {
        "id": 53406,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Blue Broadcloth Graph Check",
        "supplier_fabric_number": "CM0022MBU",
        "trinity_fabric_number": "N1-3653406",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/N1-3653406",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N1-3653406&res=300",
        "inventory_status": "In Stock",
        "pattern_id": 20,
        "weave_id": 5,
        "price_tier": 1,
        "has_image": true
    },
    {
        "id": 53407,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Pink Broadcloth Graph Check",
        "supplier_fabric_number": "CM0022PNK",
        "trinity_fabric_number": "N1-3653407",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/N1-3653407",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N1-3653407&res=300",
        "inventory_status": "In Stock",
        "pattern_id": 20,
        "weave_id": 5,
        "price_tier": 1,
        "has_image": true
    },
    {
        "id": 53408,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Red Broadcloth Graph Check",
        "supplier_fabric_number": "CM0022DRD",
        "trinity_fabric_number": "N1-3653408",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/N1-3653408",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N1-3653408&res=300",
        "inventory_status": "In Stock",
        "pattern_id": 20,
        "weave_id": 5,
        "price_tier": 1,
        "has_image": true
    },
    {
        "id": 53409,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Violet Broadcloth Graph Check",
        "supplier_fabric_number": "CM0022DPR",
        "trinity_fabric_number": "N1-3653409",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/N1-3653409",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N1-3653409&res=300",
        "inventory_status": "In Stock",
        "pattern_id": 20,
        "weave_id": 5,
        "price_tier": 1,
        "has_image": true
    },
    {
        "id": 53410,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Blue Broadcloth Graph Check",
        "supplier_fabric_number": "CM0063MBU",
        "trinity_fabric_number": "N1-3653410",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/N1-3653410",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N1-3653410&res=300",
        "inventory_status": "In Stock",
        "pattern_id": 20,
        "weave_id": 5,
        "price_tier": 1,
        "has_image": true
    }
]
```

Returns an array of fabrics.

Use this API call to lookup a fabric by trinity fabric number or supplier fabric number. We recommend using the **fabric_number** parameter to do a lookup, then pulling the first result from the array.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/fabrics`

### Query Parameters

| Parameter              | Default | Description                                                                                                                                                              |
| ---------------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| collection_id          | N/A     | Only return fabrics from a specific collection.                                                                                                                          |
| has_image              | false   | If set to true, will only return fabrics that have a working image url.                                                                                                  |
| q                      | N/A     | Wildcard matching search by trinity fabric number, supplier fabric number, fabric price code, and fabric description.                                                    |
| fabric_number          | N/A     | Show fabrics that match supplier fabric number or a trinity fabric number. The trinity fabric number is an exact match, whereas the supplier number is a wildcard match. |
| trinity_fabric_number  | N/A     | Show fabrics that match a specific Trinity fabric number.  *See below for example querying for multiple fabrics.*                                                        |
| supplier_fabric_number | N/A     | Show fabrics that match a specific Supplier fabric number.  *See below for example querying for multiple fabrics.*                                                       |
| fabric_price_code_id   | N/A     | Show fabrics that match a specific fabric price code.                                                                                                                    |
| pattern_id             | N/A     | Show fabrics that match a specific pattern ID.                                                                                                                           |
| weave_id               | N/A     | Show fabrics that match a specific weave ID.                                                                                                                             |
| price_tier             | N/A     | Show fabrics that match a specific price tier (Must be between 1-4).                                                                                                     |
| usage                  | 1       | *Description TBD*                                                                                                                                                        |
| garment_type           | 65535   | *Description TBD*                                                                                                                                                        |
| active                 | true    | If set to false, the result will also include inactive fabrics.                                                                                                          |
| show_archived          | false   | By default archived fabrics (not active, not in stock or temp out) are not returned.  Set this to true in order to show all fabrics.                                     |
| reverse_sort           | N/A     | If this parameter is set, fabrics will be sorted descending by fabric_id.                                                                                                |
| extended               | false   | If set to true, the API call returns extended objects which include a complete set of attributes and subresources.                                                       |

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
    "pattern_id": null,
    "weave_id": 3,
    "price_tier": 3,
    "has_image": false,
    "country_origin": "International",
    "fabric_grouping": "shirts",
    "pattern": null,
    "usage": "Garments",
    "last_stock_edit_date": "2018-01-19T18:36:51.000Z",
    "fabric_year": 2017,
    "fabric_garment_types": [
        "CSHT"
    ],
    "trim_garment_types": [],
    "weight": 125,
    "lead_time": "Stocked",
    "alternate_images": [
        {
            "name": "CSHT",
            "description": "Shirt Laydown",
            "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/CSHT-AS-FC4AMF-4x4?&obj=CSHT/Fabric&src=S2-3540985&res=300&obj=CSHT/Buttons&color=235,230,214&obj=CSHT/Thread&color=244,241,244&obj=CSHT/Fabric/Neckband_In&src=S2-3540985&res=300&obj=CSHT/Fabric/Collar&src=S2-3540985&res=300&obj=CSHT/Fabric/Yoke_In&src=S2-3540985&res=300&obj=CSHT/Fabric/Cuff_Out&src=S2-3540985&res=300&obj=CSHT/Fabric/Fronts/Placket&src=S2-3540985&res=300"
        }
    ],
    "collection": {
        "id": 1520,
        "name": "Soktas Bespoke V17082",
        "title": "Soktas Bespoke",
        "datecode": "V17082",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/Soktas_Bespoke_V17082?&hei=100",
        "digital_pdf_url": null
    },
    "weave": {
        "id": 3,
        "name": "dobby",
        "position": 3
    },
    "price_code": {
        "code": "S2",
        "description": "Soktas Bespoke",
        "tier": 3
    },
    "supplier": {
        "id": 57,
        "code": "SK",
        "name": "Soktas",
        "city": "Aydin",
        "state": null,
        "country": "Turkey"
    },
    "composition": {
        "id": 13,
        "description": "100% Cotton"
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
        "id": 38992,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Lt Blue Solid",
        "supplier_fabric_number": "FL51168-13",
        "trinity_fabric_number": "Z8-3338992",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z8-3338992",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z8-3338992&res=300",
        "inventory_status": "In Stock",
        "pattern_id": 1,
        "weave_id": null,
        "price_tier": 4,
        "has_image": true
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
        "inventory_status": "In Stock",
        "pattern_id": 18,
        "weave_id": null,
        "price_tier": 4,
        "has_image": true
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
        "inventory_status": "In Stock",
        "pattern_id": 18,
        "weave_id": null,
        "price_tier": 4,
        "has_image": true
    },
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
        "inventory_status": "In Stock",
        "pattern_id": 44,
        "weave_id": null,
        "price_tier": 4,
        "has_image": true
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
        "inventory_status": "In Stock",
        "pattern_id": 2,
        "weave_id": null,
        "price_tier": 4,
        "has_image": true
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
        "inventory_status": "In Stock",
        "pattern_id": 2,
        "weave_id": null,
        "price_tier": 4,
        "has_image": true
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
        "inventory_status": "In Stock",
        "pattern_id": 22,
        "weave_id": null,
        "price_tier": 4,
        "has_image": true
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
        "inventory_status": "In Stock",
        "pattern_id": 1,
        "weave_id": null,
        "price_tier": 4,
        "has_image": true
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
        "inventory_status": "In Stock",
        "pattern_id": 2,
        "weave_id": null,
        "price_tier": 4,
        "has_image": true
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
        "inventory_status": "In Stock",
        "pattern_id": 2,
        "weave_id": null,
        "price_tier": 4,
        "has_image": true
    }
]
```

Returns a list of related fabrics

### HTTP Request

`GET https://api.trinity-apparel.com/v1/fabrics/:id/related`

### Query Parameters

| Parameter | Default | Description                                                                                                        |
| --------- | ------- | ------------------------------------------------------------------------------------------------------------------ |
| id        | N/A     | The specific fabric id you want to see related fabrics for.                                                        |
| rpp       | 10      | The number of results you would like to return.                                                                    |
| extended  | false   | If set to true, the API call returns extended objects which include a complete set of attributes and subresources. |

### Other

- Permissions: All
- Pagination: N/A
