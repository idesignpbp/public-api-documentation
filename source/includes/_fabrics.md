# Fabrics API

## Fabric Resources

The Trinity Fabrics API provides detailed information on fabrics and collections.  Collections are groups of fabrics.  Here is a detailed list of attributes in those resources:

### Fabric

```json
# Standard Object - Used in a resource collection
{
    "id": 25600,
    "active": true,
    "in_stock": 1,
    "restock_date": null,
    "description": "Fawn Solid",
    "supplier_fabric_number": "8427",
    "trinity_fabric_number": "U7-3025600",
    "url": "https://s7d4.scene7.com/is/image/trinityapparel/U7-3025600",
    "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=U7-3025600&res=300",
    "inventory_status": "In Stock",
    "pattern_id": 1,
    "weave_id": null,
    "price_tier": 3,
    "discount": null,
    "has_image": false,
    "availability": "single-cut",
    "favorite_id": null,
    "fabric_garment_type": 199,
    "trim_garment_type": 0
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
| discount <br> <span>integer</span>              | If present, will be the percentage off the price of the fabric.                                                                                                                                                              |
| has_image <br> <span>boolean</span>             | If true, the fabric image url will actually return an image of the fabric.                                                                                                                                                   |
| availability <br> <span>string</span>           | One of: "At Once", meaning the fabric is ready (4-5 week delivery for clothing, 2-3 week delivery for shirts), or "Single Cut", meaning the fabric is not yet at the factory (5-6 weeks for clothing, 3-5 weeks for shirts), "Temp Out", meaning the fabrics have been reordered but will not be restocked for some time, or "Sold Out", meaning the fabrics are neither stocked nor reordered.|
| favorite_id <br> <span>integer</span>           | If set, the fabric has been favorited by the client in fabrics explorer. ID can be used to unfavorite a fabric.                                                                                                              |
| fabric_garment_type <br> <span>integer</span>   | A bitmask describing what types of garments the fabric can be used for. See advanced queries.                                                                                                                                |
| trim_garment_type <br> <span>integer</span>     | A bitmask describing what types of linings the fabric can be used for. See advanced queries.                                                                                                                                 |

```json
# Extended Object
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
    "discount": null,
    "has_image": false,
    "availability": "single-cut",
    "favorite_id": null,
    "fabric_type": null,
    "fabric_garment_type": 231,
    "trim_garment_type": 0,
    "country_origin": "International",
    "fabric_grouping": "black",
    "pattern": "solid",
    "usage": "Garments",
    "last_stock_edit_date": null,
    "fabric_year": 2019,
    "fabric_garment_types": ...,
    "trim_garment_types": ...,
    "weight": 212,
    "lead_time": "3 - 10 days",
    "alternate_images": ...,
    "related_trim": null,
    "identical_fabrics": [],
    "collection": ...,
    "fabric_pattern": ...,
    "fabric_weave": ...,
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
| usage <br> <span>integer</span>                    | The usage of the fabric (E.g., Shirt Trim, Clothing Trim, etc).       |
| last_stock_edit_date <br> <span>datetime</span>    | The last time the fabric inventory level was changed.                 |
| fabric_year <br> <span>year</span>                 | The year the fabric was released.                                     |
| fabric_garment_types <br> <span>subresource</span> | An array of the garment types a fabric is used for.                   |
| trim_garment_types <br> <span>subresource</span>   | An array of the garment types a trim is used for.                     |
| weight <br> <span>integer</span>                   | Weight in grams per square meter.                                     |
| lead_time <br> <span>string</span>                 | If the fabric is in stock or the estimated time until it is in stock. |
| alternate_images <br> <span>subresource</span>     | An array of alternate images for a fabric.                            |
| related_trim <br> <span>subresource</span>         | A fabric subresource detailing the trim/lining related to the fabric. |
| identical_fabrics <br> <span>subresource</span>    | An array of fabrics identical to this one.                            |
| collection <br> <span>subresource</span>           | The collection in which the fabric was released.                      |
| fabric_pattern <br> <span>subresource</span>       | Information about the pattern of a fabric, such as `stripe`, `check`, and `solid`. |
| fabric_weave <br> <span>subresource</span>         | Information about the weave of a fabric.                              |
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

### Pattern

```json
# Standard Object - Used in a resource collection
{
    "id": 3,
    "name": "check",
    "position": 3,
    "parent_pattern_id": null
}
```

Standard Attributes

| Attribute                          | Description                       |
| ---------------------------------- | --------------------------------- |
| id <br> <span>integer</span>       | Unique identifier for the object. |
| name <br> <span>string</span>      | The name of the pattern.            |
| position <br> <span>integer</span> | The ordering of the pattern in a list. |
| parent_pattern_id <br> <span>integer</span> | Points to a higher level grouping of patterns, such as checks.  For example, a child could be Club Check. |

### Weave

```json
# Standard Object - Used in a resource collection
{
    "id": 4,
    "name": "poplin",
    "position": 4,
    "parent_weave_id": null
}
```

Standard Attributes

| Attribute                          | Description                       |
| ---------------------------------- | --------------------------------- |
| id <br> <span>integer</span>       | Unique identifier for the object. |
| name <br> <span>string</span>      | The name of the weave.            |
| position <br> <span>integer</span> | The ordering of the weave in a list. |
| parent_weave_id <br> <span>integer</span> | Points to a higher level grouping of weaves |

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
    "digital_pdf_url": "https://workflow.trinity-apparel.com/share/view_document.php?use_ltype=trinity&document_id=281&download=1&filename=Derby_Performance_Cornerstone_V17011.pdf"
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
| digital_pdf_url <br> <span>string</span>      | URL to a pdf booklet of the collection.                                                                                          |

```json
# Extended Object
```json
{
    "id": 1854,
    "name": "Outerwear V18082",
    "title": "Outerwear",
    "datecode": "V18082",
    "image": "https://s7d4.scene7.com/is/image/trinityapparel/Outerwear_V18082?&hei=100",
    "digital_pdf_url": "https://trinity-apparel.s3.amazonaws.com/assets/digital_collection_outerwear_18082.pdf",
    "description": "",
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
        "id": 2,
        "name": "07 FW Bellagio",
        "title": "07 FW Bellagio",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_FW_Bellagio?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 3,
        "name": "07 FW Governors",
        "title": "07 FW Governors",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_FW_Governors?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 4,
        "name": "07 FW Heritage Classic",
        "title": "07 FW Heritage Classic",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_FW_Heritage_Classic?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 5,
        "name": "07 FW Heritage Fashion",
        "title": "07 FW Heritage Fashion",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_FW_Heritage_Fashion?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 6,
        "name": "07 FW Kensington I",
        "title": "07 FW Kensington I",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_FW_Kensington_I?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 7,
        "name": "07 FW Kensington II",
        "title": "07 FW Kensington II",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_FW_Kensington_II?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 8,
        "name": "07 FW Lords",
        "title": "07 FW Lords",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_FW_Lords?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 9,
        "name": "07 FW Trofeo",
        "title": "07 FW Trofeo",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_FW_Trofeo?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 10,
        "name": "07 FW Zenith Cashmere",
        "title": "07 FW Zenith Cashmere",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_FW_Zenith_Cashmere?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 11,
        "name": "07 SS Cambridge",
        "title": "07 SS Cambridge",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_SS_Cambridge?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 12,
        "name": "07 SS Governors",
        "title": "07 SS Governors",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_SS_Governors?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 13,
        "name": "07 SS Heritage Classic",
        "title": "07 SS Heritage Classic",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_SS_Heritage_Classic?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 14,
        "name": "07 SS Heritage Fashion",
        "title": "07 SS Heritage Fashion",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_SS_Heritage_Fashion?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 15,
        "name": "07 SS Lords",
        "title": "07 SS Lords",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_SS_Lords?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 16,
        "name": "07 SS Queensborough",
        "title": "07 SS Queensborough",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_SS_Queensborough?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 17,
        "name": "07 SS Thomas",
        "title": "07 SS Thomas",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_SS_Thomas?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 18,
        "name": "07 SS Yorkshire",
        "title": "07 SS Yorkshire",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_SS_Yorkshire?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 19,
        "name": "07 SS Zenith",
        "title": "07 SS Zenith",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/07_SS_Zenith?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 20,
        "name": "08 SS Barberis",
        "title": "08 SS Barberis",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/08_SS_Barberis?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 21,
        "name": "08 SS Florence Cottons",
        "title": "08 SS Florence Cottons",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/08_SS_Florence_Cottons?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 22,
        "name": "08 SS Florence Gabardines",
        "title": "08 SS Florence Gabardines",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/08_SS_Florence_Gabardines?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 23,
        "name": "08 SS Heritage I",
        "title": "08 SS Heritage I",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/08_SS_Heritage_I?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 24,
        "name": "08 SS Heritage II",
        "title": "08 SS Heritage II",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/08_SS_Heritage_II?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 25,
        "name": "08 SS Jamison Fancies",
        "title": "08 SS Jamison Fancies",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/08_SS_Jamison_Fancies?&hei=100",
        "digital_pdf_url": null
    },
    {
        "id": 26,
        "name": "08 SS Jamison Flannels",
        "title": "08 SS Jamison Flannels",
        "datecode": "",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/08_SS_Jamison_Flannels?&hei=100",
        "digital_pdf_url": null
    }
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
    "digital_pdf_url": "https://trinity-apparel.s3.amazonaws.com/assets/digital_collection_outerwear_18082.pdf",
    "description": null,
    "fabrics": [
        {
            "id": 54921,
            "active": true,
            "in_stock": 0,
            "restock_date": null,
            "description": "Blue Navy Plaid",
            "supplier_fabric_number": "BT65151-1",
            "trinity_fabric_number": "C4-3754921",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/C4-3754921",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3754921&res=300",
            "inventory_status": "Sold Out",
            "pattern_id": 4,
            "weave_id": null,
            "price_tier": 1,
            "discount": null,
            "has_image": true,
            "availability": "out of stock",
            "favorite_id": null,
            "fabric_type": null,
            "fabric_garment_type": 231,
            "trim_garment_type": 0
        },
        .
        .
        .,
        {
            "id": 54966,
            "active": true,
            "in_stock": 1,
            "restock_date": null,
            "description": "Black Solid",
            "supplier_fabric_number": "9901-7",
            "trinity_fabric_number": "K3-3754966",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/K3-3754966",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=K3-3754966&res=300",
            "inventory_status": "In Stock",
            "pattern_id": 1,
            "weave_id": null,
            "price_tier": 3,
            "discount": null,
            "has_image": true,
            "availability": "single-cut",
            "favorite_id": null,
            "fabric_type": null,
            "fabric_garment_type": 231,
            "trim_garment_type": 0
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
        "id": 25600,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Fawn Solid",
        "supplier_fabric_number": "8427",
        "trinity_fabric_number": "U7-3025600",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/U7-3025600",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=U7-3025600&res=300",
        "inventory_status": "In Stock",
        "pattern_id": 1,
        "weave_id": null,
        "price_tier": 3,
        "discount": null,
        "has_image": false,
        "availability": "single-cut",
        "favorite_id": null,
        "fabric_type": null,
        "fabric_garment_type": 199,
        "trim_garment_type": 0
    },
    {
        "id": 26880,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Taupe Paisley",
        "supplier_fabric_number": "CH-1898-27",
        "trinity_fabric_number": "L2-3026880",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/L2-3026880",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=L2-3026880&res=300",
        "inventory_status": "In Stock",
        "pattern_id": 36,
        "weave_id": null,
        "price_tier": 1,
        "discount": null,
        "has_image": true,
        "availability": "at once",
        "favorite_id": null,
        "fabric_type": null,
        "fabric_garment_type": 247,
        "trim_garment_type": 759
    },
    .
    .
    .,
    {
        "id": 39936,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Pink Woven Herringbone",
        "supplier_fabric_number": "ST 64486-85",
        "trinity_fabric_number": "S3-3339936",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/S3-3339936",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=S3-3339936&res=300",
        "inventory_status": "In Stock",
        "pattern_id": null,
        "weave_id": 2,
        "price_tier": 3,
        "discount": null,
        "has_image": true,
        "availability": "single-cut",
        "favorite_id": null,
        "fabric_type": null,
        "fabric_garment_type": 8,
        "trim_garment_type": 0
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
| pattern_id             | N/A     | Show fabrics that match a specific pattern, plus all child patterns of that id |
| weave_id               | N/A     | Show fabrics that match a specific weave, plus all child patterns of that id |
| price_tier             | N/A     | Show fabrics that match a specific price tier (Must be between 1-4).                                                                                                     |
| usage                  | 1       | An integer between 1 and 7. fabric usage can be clothing, shirting, lining, shirt trim, or a combination of these values |
| garment_type           | N/A     | An integer between 1 and 1023. garment_type is a bitmask which allows us to turn on and off different garment types, such as pant and shirt easily |
| trim_garment_type      | N/A     | An integer between 1 and 1023. garment_type is a bitmask which allows us to turn on and off different trim garment types, such as shirt trim or jacket lining easily |
| active                 | true    | If set to false, the result will also include inactive fabrics.                                                                                                          |
| show_archived          | false   | By default archived fabrics (not active, not in stock or temp out) are not returned.  Set this to true in order to show all fabrics.                                     |
| reverse_sort           | N/A     | If this parameter is set, fabrics will be sorted descending by fabric_id.                                                                                                |
| extended               | false   | If set to true, the API call returns extended objects which include a complete set of attributes and subresources.                                                       |
| in_stock               | N/A     | If set, filters by fabric availability; 0, 1, and 2 meaning Sold Out, In Stock, and Temp Out respectively.                                                               |

### Other

- Permissions: All
- Pagination: Yes

### Querying by multiple fabric numbers

In order to query for multiple fabric numbers, you will pass in multiple params with the array-style format like below:

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
    "discount": null,
    "has_image": false,
    "availability": "at once",
    "favorite_id": null,
    "fabric_type": null,
    "fabric_garment_type": 8,
    "trim_garment_type": 0,
    "country_origin": "International",
    "fabric_grouping": "shirts",
    "pattern": "solid",
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
            "name": "Shirt",
            "code": "CSHT",
            "description": "Shirt Laydown",
            "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/CSHT-AS-FC4AMF-4x4?&obj=CSHT/Fabric&src=S2-3540985&res=300&obj=CSHT/Buttons&color=235,230,214&obj=CSHT/Thread&color=244,241,244&obj=CSHT/Fabric/Neckband_In&src=S2-3540985&res=300&obj=CSHT/Fabric/Collar&src=S2-3540985&res=300&obj=CSHT/Fabric/Yoke_In&src=S2-3540985&res=300&obj=CSHT/Fabric/Cuff_Out&src=S2-3540985&res=300&obj=CSHT/Fabric/Fronts/Placket&src=S2-3540985&res=300"
        }
    ],
    "related_trim": null,
    "identical_fabrics": [],
    "collection": {
        "id": 1520,
        "name": "Soktas Bespoke V17082",
        "title": "Soktas Bespoke",
        "datecode": "V17082",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/Soktas_Bespoke_V17082?&hei=100",
        "digital_pdf_url": null
    },
    "fabric_pattern": null,
    "fabric_weave": {
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

## Advanced Fabric Queries

```shell
curl "https://api.trinity-apparel.com/v1/fabrics?in_stock=2&collection_id=1812"
  -H "Authorization Bearer: swaledale"
```

> The above command returns Temp Out fabrics from collection 1812

```shell
curl "https://api.trinity-apparel.com/v1/fabrics?in_stock=1&price_tier=4"
  -H "Authorization Bearer: swaledale"
```

> The above command returns all expensive in stock fabrics


```shell
curl "https://api.trinity-apparel.com/v1/fabrics?garment_type=5&usage=1"
  -H "Authorization Bearer: swaledale"
```

> The above command returns Suiting, i.e. Coat (1) + Pant (4) = 5, usage Garment (1)

```shell
curl "https://api.trinity-apparel.com/v1/fabrics?trim_garment_type=1&usage=4"
  -H "Authorization Bearer: swaledale"
```

> The above command returns Lining, i.e. Jackets (1), usage Clothing Trim (4)

```shell
curl "https://api.trinity-apparel.com/v1/fabrics?garment_type=8&usage=1"
  -H "Authorization Bearer: swaledale"
```

> The above command returns Shirting, i.e. Shirts (8), usage Garment (1)

```shell
curl "https://api.trinity-apparel.com/v1/fabrics?trim_garment_type=8&usage=2"
  -H "Authorization Bearer: swaledale"
```

> The above command returns Shirt trims, i.e. Shirts (8), usage Shirt Trims (2)

```shell
curl "https://api.trinity-apparel.com/v1/fabrics?garment_type=32&usage=1"
  -H "Authorization Bearer: swaledale"
```

> The above command returns Outerwear, i.e. Outerwear (32), usage Garment (1)

```shell
curl "https://api.trinity-apparel.com/v1/fabrics?pattern_id=5"
  -H "Authorization Bearer: swaledale"
```

> The above command returns fabrics of the "print" pattern

```shell
curl "https://api.trinity-apparel.com/v1/fabrics?weave_id=2"
  -H "Authorization Bearer: swaledale"
```

> The above command returns fabrics of the "herrinbone" weave

Search by garment type, usage, stock availability, and price tier.

### Query Parameters

| Parameter           | Description                                                                       |
| ------------------- | --------------------------------------------------------------------------------- |
| garment_type        | A bitmask to search for fabrics that are used by particular garment types         |
| trim_garment_type   | A bitmask to search for fabrics that are used as trim in particular garment types |
| usage               | A bitmask to search fabrics by usage, e.g. garment, shirt trim, or clothing trim  |
| in_stock            | Either 0, sold out, 1, in stock, or 2, temp out                                   |
| price_tier          | 1-4, 4 being most expensive                                                       |
| pattern_id          | Filter by pattern, see table below                                                |
| weave_id            | Filter by weave, see table below                                                  |

### Garment Bitmask

Works the same for trims.

| Garment Type        | Bitmask |
| ------------------- | ------- |
| GARMENT_COAT        | 1       |
| GARMENT_VEST        | 2       |
| GARMENT_PANT        | 4       |
| GARMENT_SHIRT       | 8       |
| GARMENT_PANT2       | 16      |
| GARMENT_TOPCOAT     | 32      |
| GARMENT_SHORT       | 64      |
| GARMENT_BREEK       | 128     |
| GARMENT_TIE         | 256     |
| GARMENT_SWK         | 512     |
| GARMENT_ALLSUIT     | GARMENT_COAT OR GARMENT_VEST OR GARMENT_PANT OR GARMENT_SHORT OR GARMENT_BREEK OR GARMENT_SWK |
| GARMENT_ALL         | GARMENT_COAT OR GARMENT_VEST OR GARMENT_PANT OR GARMENT_TOPCOAT OR GARMENT_SHORT OR GARMENT_BREEK OR GARMENT_SHIRT OR GARMENT_SWK |
| GARMENT_ALLPANT     | GARMENT_PANT OR GARMENT_SHORT OR GARMENT_BREEK |
| GARMENT_ALLCOAT     | GARMENT_COAT OR GARMENT_TOPCOAT |
| GARMENT_ALLCLOTHING | GARMENT_ALLSUIT OR GARMENT_TOPCOAT OR GARMENT_PANT2 |

(OR here is Bitwise OR)

### Fabric Usage Bitmask

| Usage           | Bitmask |
|-----------------|---------|
| USAGE_GARMENT   | 1       |
| USAGE_SHIRT_TRIM | 2      |
| USAGE_CLOTHING_TRIM | 4   |
| USAGE_ALL       | USAGE_GARMENT OR USAGE_SHIRT_TRIM OR USAGE_CLOTHING_TRIM | 

(OR here is Bitwise OR)

### Patterns to Use

| Pattern         | ID   |
|-----------------|------|
| solid           | 1    |
| stripe          | 2    |
| check           | 3    |
| plaid           | 4    |
| print           | 5    |
| windowpane      | 6    |
| other           | 7    |

### Weaves to Use

| Weave           | ID   |
|-----------------|------|
| plain           | 1    |
| herringbone     | 2    |
| dobby           | 3    |
| poplin          | 4    |
| broadcloth      | 5    |
| chambray        | 6    |
| twill           | 7    |
| basket          | 8    |
| other           | 9    |

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
        "inventory_status": "In Stock",
        "pattern_id": 44,
        "weave_id": null,
        "price_tier": 4,
        "discount": null,
        "has_image": true,
        "availability": "single-cut",
        "favorite_id": null,
        "fabric_type": null,
        "fabric_garment_type": 8,
        "trim_garment_type": 0
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
        "inventory_status": "In Stock",
        "pattern_id": 1,
        "weave_id": null,
        "price_tier": 4,
        "discount": null,
        "has_image": true,
        "availability": "single-cut",
        "favorite_id": null,
        "fabric_type": null,
        "fabric_garment_type": 8,
        "trim_garment_type": 0
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
        "discount": null,
        "has_image": true,
        "availability": "single-cut",
        "favorite_id": null,
        "fabric_type": null,
        "fabric_garment_type": 8,
        "trim_garment_type": 0
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
        "discount": null,
        "has_image": true,
        "availability": "single-cut",
        "favorite_id": null,
        "fabric_type": null,
        "fabric_garment_type": 8,
        "trim_garment_type": 0
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
        "discount": null,
        "has_image": true,
        "availability": "single-cut",
        "favorite_id": null,
        "fabric_type": null,
        "fabric_garment_type": 8,
        "trim_garment_type": 0
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
        "discount": null,
        "has_image": true,
        "availability": "single-cut",
        "favorite_id": null,
        "fabric_type": null,
        "fabric_garment_type": 8,
        "trim_garment_type": 0
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
        "discount": null,
        "has_image": true,
        "availability": "single-cut",
        "favorite_id": null,
        "fabric_type": null,
        "fabric_garment_type": 8,
        "trim_garment_type": 0
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
        "discount": null,
        "has_image": true,
        "availability": "single-cut",
        "favorite_id": null,
        "fabric_type": null,
        "fabric_garment_type": 8,
        "trim_garment_type": 0
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
        "discount": null,
        "has_image": true,
        "availability": "single-cut",
        "favorite_id": null,
        "fabric_type": null,
        "fabric_garment_type": 8,
        "trim_garment_type": 0
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
        "discount": null,
        "has_image": true,
        "availability": "single-cut",
        "favorite_id": null,
        "fabric_type": null,
        "fabric_garment_type": 8,
        "trim_garment_type": 0
    }
]
```

Returns a list of up to 10 related fabrics.

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

### Sorting Algorithm

- Usage (shirting, clothing, trim, lining)
- Garment types
- Exact match on fabric description
- Pattern and weave
- Price Code
- Mill
- Composition
- Weight in g/m
- Cost
- Date Added
