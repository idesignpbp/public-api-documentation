# Manufacturers API

The manufacturers API allows a factory to download all relevant information needed to produce a garment. Plus it allows the factory to update the status of a garment and add the garment to a shipment.

This includes:

- [Download Garments](#download-garments) - a list of new garment orders that are ready to be produced by the factory
- [Garment Detail](#get-a-specific-garment)
- [Garment Properties](#garment-properties) - Get Measurements, Options and Materials for a specific garment [**Recently Updated!**]
- [Get All Embroidery](#get-all-embroidery) - Get embroidery from a specific date range or list of garments
- [Get Specific Embroidery](#get-specific-embroidery) -Get all embroidery on a specific garment
- [Update Fabric](#update-fabric) - Set cuttable width, pattern type and width, and other fabric attributes.
- [Create Fabric Cut](#create-fabric-cut) - Enter CAD measurements for a single fabric used to make a garment
- [Get Fabric Cuts](#get-fabric-cuts) - Get a list of all fabrics ready to be cut by a manufacturer
- [Update Fabric Cut](#update-fabric-cut) - Mark a specific fabric as cut
- [Set Order Status](#set-order-status) - E.g., Move a garment from Ready to Production

Deprecated:

- [Garment Fabrics](#get-garment-fabrics) - Get a list of fabrics needed, what they are used for (shell, lining, trims, etc), and see their measurments and status

## Order Processing Flow

`Ready` -> `Blue Pencil` -> `Cutting` -> `Production` -> `Production Complete` -> `International Transit`

### Ready status

Garment can be downloaded if it is not in a delay status (trinity review of special instructions, etc). Downloading involves getting garment detail, garment properties, garment fabrics, and downloading the gerber files.

Once the garment is fully downloaded, the manufacturer should move the garment to Blue Pencil status (ID=4 or code=PENDING).

### Blue Pencil status

In Blue Pencil status, the CAD team lays the marker, the order team puts the order in the production plan, and materials are gathered. Once the marker is complete, the factory should input the CAD measurements into Trinity Admin on the `Fabric Cuts` page: https://admin.trinity-apparel.com/fabric_cuts

When all fabric cut lengths are entered into the system, the garment will be automatically moved into cutting.

### Cutting status

Once all fabrics (shell, lining, trims, etc) have been cut, the garment should be moved to Production status (ID=5 or code=PRODUCTION) using the set order status call.

### Production status

During the production process we print care labels and hang tags. You will use our Windows applications to print these. These applications require internet connectivity to hit our api and get data about the garment.

For garments with embroidery, you need to use two Windows applications. One must be connected to a computer with the App Ethos software installed and have the App Ethos dongle. It cannot be a server and will not allow remote desktop connections while the app is running. Our app connects to our API and gets data about embroidery and generates an input file that app ethos uses to create a DST file. The file can either sit on a share drive or be moved manually using a USB key. The second embroidery app reads the DST files and provides them to a Brother embroidery machine.

Once production is complete and the garment is ready to ship. Please set the order status to production complete (ID=6 or code=MADE).

### Production complete status

In the production complete status, we build a packing list using the create shipment call. We can add a tracking number immediately or add one at a later time. Once the shipment has a tracking number, we can move the garments to international transit (set status to ID=7 or code=SHIPDC).

### International Transit status

Trinity will take the order from here. Once we receive the garment at a distribution center, we will move the status to final inspection.

## Resources

The resources provided by the manufacturers API are almost identical to the orders API. Only the garment and dealer_order objects are different. Links to download Gerber input files and the order PDFs are included.

### Garment

```json
# Garment Object - Used in a resource collection
{
    "id": 845556,
    "title": "TEST-845556",
    "order_id": 386627,
    "copied_garment_id": null,
    "garment_type": "SWK",
    "prefix": "TEST",
    "index": "1",
    "created_at": "2018-04-24T21:17:23.000Z",
    "updated_at": null,
    "last_status_change_date": "2018-04-24T21:17:23.000Z",
    "last_delay_change_date": null,
    "links": {
        "gerber": "http://localhost:8080/share/order_insert.php?suit_ids[]=845556&units=uscust&format=gerber&fabtype=both",
        "order_insert": "https://trinity-apparel.com/share/order_insert.php?format=pdfzip&units=si&suit_ids%5B%5D=845556",
        "order_split": "https://documents.trinity-apparel.com/order_splits?garment_id=845556&locale=en"
    },
    "manufacturer": ...,
    "fabric":       ...,
    "order_status": ...,
    "delay_status": ...,
    "dealer_order": ...
}
```

Standard Attributes

| Attribute                                          | Description                                                                                                      |
| -------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| id <br> <span>integer</span>                       | Unique identifier for the object                                                                                 |
| title <br> <span>string</span>                     | Our SKU field which includes the garment id number and information about where the factory will send the garment |
| order_id <br> <span>integer</span>                 | Each garment must be a part of a specific order                                                                  |
| copied_garment_id <br> <span>integer</span>        | Garment id if this was copied from a previous order                                                              |
| garment_type <br> <span>string</span>              | Type of garment. [Click here](#garment-types) for more info                                                      |
| prefix <br> <span>string</span>                    | First part of the title. This indicates where the order was made or where the factory will send the garment      |
| index <br> <span>string</span>                     | Sequence number (1/7, 2/7, 3/7 ...) for each garment in an order. Each item has a different index                |
| created_at <br> <span>datetime</span>              | When the garment was first created (but not ordered)                                                             |
| updated_at <br> <span>datetime</span>              | When the garment was last modified                                                                               |
| last_status_change_date <br> <span>datetime</span> | When did the order status last change to a new state                                                             |
| last_delay_change_date <br> <span>datetime</span>  | When did the delay status last change to a new state                                                             |
| links <br> <span>subresource</span>                | Urls that allow the manufacturer to generate Gerber ASCII files, an Order Insert PDF, and an Order Split         |
| manufacturer <br> <span>subresource</span>         | Factory that made the order. [Click here](#manfacturers) for more info                                           |
| fabric <br> <span>subresource</span>               | Shell fabric used in the order. [Click here](#fabrics) for more info                                             |
| order_status <br> <span>subresource</span>         | Current status of the order. [Click here](#order-statuses) for more info                                         |
| delay_status <br> <span>subresource</span>         | If garment is delayed, this will return why. [Click here](#delay-statuses) for more info                         |
| dealer_order <br> <span>subresource</span>         | The full order placed by a single customer. Includes this garment and can include more garments.                 |

### Dealer Order

```json
# Order Object - Used in a resource collection
{
    "id": 386627,
    "title": "DO-386627",
    "custom_order_number": "",
    "garment_count": 0,
    "ship_type": "Ground",
    "measurement_units": "uscust",
    "ordered_at": null,
    "created_at": "2018-04-24T20:36:28.000Z",
    "invoiced_at": null
}
```

Standard Attributes

| Attribute                                    | Description                                                                                                  |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| id <br> <span>string</span>                  | Unique identifier for the object                                                                             |
| title <br> <span>string</span>               | Our SKU field for orders                                                                                     |
| custom_order_number <br> <span>string</span> | Dealers can set this field to whatever they want. It is typically the dealer's SKU or a summary of the order |
| garment_count <br> <span>integer</span>      | How many garments are in the order. multi-piece garments (e.g., Suit) are counted as 1.                      |
| ship_type <br> <span>string</span>           | How is the garment shipped to the final destination                                                          |
| measurement_units <br> <span>string</span>   | Units can be `uscust` for US customary units (in) or `si` for metric units (cm)                              |  |
| ordered_at <br> <span>datetime</span>        | Time that the dealer completed the checkout process and officially placed the order                          |
| created_at <br> <span>datetime</span>        | Time when the dealer first began adding garments to the order                                                |
| invoiced_at <br> <span>datetime</span>       | Time of the first invoice                                                                                    |

### Embroidery

```json
# Embroidery Object - Used in collections
{
    "garment": {
        "id": 1081783,
        "manufacturer_id": 4,
        "garment_type": 1,
        "created_at": "2019-11-03T18:47:22.000Z"
    },
    "option": {
        "id": 89,
        "name": "customer_label_text",
        "garment_type": 1,
        "garment_types": [
            "csc"
        ]
    },
    "text": "M Kiser",
    "font": "Calligraphy",
    "color": "5-01 White",
    "position": "T4 - Left Below Breast Pkt",
    "size": null
}
```

| Attribute                             | Description                                                            |
| ------------------------------------- | ---------------------------------------------------------------------- |
| garment <br> <span>subresource</span> | Limited info on the garment                                            |
| fabric <br> <span>subresource</span>  | Limited info on the fabric                                             |
| text <br> <span>string</span>         | Text for the embroidery                                                |
| font <br> <span>string</span>         | Embroidery font or Monogram selected                                   |
| color <br> <span>string</span>        | Thread color                                                           |
| position <br> <span>string</span>     | Location for the embroidery; Only required for some embroidery options |
| size <br> <span>string</span>         | Width of the embroidery                                                |

### Embroidery Garment

```json
# Minimal Garment Object - Used in embroidery
{
    "id": 1081783,
    "manufacturer_id": 4,
    "garment_type": 1,
    "created_at": "2019-11-03T18:47:22.000Z"
}
```

Standard Attributes

| Attribute                                 | Description                                                 |
| ----------------------------------------- | ----------------------------------------------------------- |
| id <br> <span>integer</span>              | Unique identifier for the garment                           |
| manufacturer_id <br> <span>integer</span> | The factory who made the garment                            |
| garment_type <br> <span>integer</span>    | Garment bitmask. [Click here](#garment-types) for more info |
| created_at <br> <span>datetime</span>     | When the garment was first created (but not ordered)        |

### Embroidery Option

```json
# Minimal Option Object - Used in embroidery
{
    "id": 89,
    "name": "customer_label_text",
    "garment_type": 1,
    "garment_types": [
        "csc"
    ]
}
```

Standard Attributes

| Attribute                              | Description                                                     |
| -------------------------------------- | --------------------------------------------------------------- |
| id <br> <span>integer</span>           | Unique identifier for the option                                |
| name <br> <span>string</span>          | Option name. Typically refers to the location of the embroidery |
| garment_type <br> <span>integer</span> | Garment bitmask. [Click here](#garment-types) for more info     |
| garment_types <br> <span>array</span>  | List of human readable garment types                            |
| created_at <br> <span>datetime</span>  | When the garment was first created (but not ordered)            |

### Fabric Cut

```json
# Fabric Cut Object - Used in collections
{
    "id": 540803,
    "is_cut": false,
    "created_at": "2019-10-28T07:25:55.000Z",
    "length": 415,
    "actual_length": 410,
    "width": 136,
    "garment": {
        "id": 1059195,
        "title": "ID-1059195",
        "created_at": "2019-09-13T06:23:02.000Z",
        "garment_type": "CCVP"
    },
    "fabric": {
        "id": 29938,
        "description": "Medium Blue Paisley",
        "trinity_fabric_number": "L6-3129938",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/L6-3129938",
        "has_image": true
    },
    "option": {
        "id": 229,
        "name": "lining_fabric_num",
        "description": "Lining Fabric #"
    }
}
```

| Attribute                             | Description                                                                                                                                       |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| garment <br> <span>subresource</span> | Each garment record contains the id, title, date the garment was first entered into the system, and a garment type code                           |
| fabric <br> <span>subresource</span>  | Limited info on the fabric (id, description trinity number, a url for a repeatable swatch image, and a boolean to show if the image is available) |
| fabric <br> <span>subresource</span>  | Limited info on the option (id, name, and description). Can be null                                                                               |
| id <br> <span>integer</span>          | Unique identifier for the fabric cut                                                                                                              |
| is_cut <br> <span>boolean</span>      | Has the cut been made?                                                                                                                            |
| length <br> <span>float</span>        | Length in centimeters (5 cm added to input, so the factory has overage)                                                                           |
| actual_length <br> <span>float</span> | Actual length in centimeters                                                                                                                      |
| width <br> <span>float</span>         | Width in centimeters                                                                                                                              |
| created_at <br> <span>datetime</span> | When was the cut record added                                                                                                                     |

## Download Garments

```shell
curl "https://api.trinity-apparel.com/v1/download_garments"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 1108277,
        "title": "ID-1108277",
        "order_id": 509309,
        "copied_garment_id": null,
        "garment_type": "CCVP",
        "prefix": "ID",
        "index": "1/1",
        "created_at": "2020-01-13T10:01:23.000Z",
        "updated_at": null,
        "last_status_change_date": "2020-01-13T10:04:34.000Z",
        "last_delay_change_date": null,
        "links": {
            "gerber": "http://localhost:8080/share/order_insert.php?suit_ids[]=1108277&units=uscust&format=gerber&fabtype=both",
            "order_insert": "https://trinity-apparel.com/share/order_insert.php?format=pdfzip&units=si&suit_ids%5B%5D=1108277",
            "order_split": "https://documents.trinity-apparel.com/order_splits?garment_id=1108277&locale=en"
        },
        "manufacturer": {
            "id": 5,
            "name": "Trisco TAM",
            "email": "info@trinity-apparel.com"
        },
        "fabric": {
            "id": 70215,
            "active": true,
            "in_stock": 1,
            "restock_date": null,
            "description": "Blue Sharkskin",
            "supplier_fabric_number": "100325",
            "trinity_fabric_number": "TT-3970215",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/TT-3970215",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=TT-3970215&res=300",
            "inventory_status": "In Stock",
            "pattern_id": null,
            "weave_id": 15,
            "price_tier": null,
            "discount": null,
            "has_image": false,
            "availability": "at once",
            "favorite_id": null,
            "fabric_type": null,
            "fabric_garment_type": 711,
            "trim_garment_type": 0
        },
        "order_status": {
            "code": "READY",
            "name": "Pending",
            "description": "Ready"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 509309,
            "title": "DO-509309",
            "custom_order_number": null,
            "garment_count": 1,
            "ship_type": "In-Store Pick-Up",
            "measurement_units": "uscust",
            "ordered_at": "2020-01-13T10:04:34.000Z",
            "created_at": "2020-01-13T10:00:47.000Z",
            "invoiced_at": null
        },
        "outgoing_address": {
            "id": 1,
            "contact_name": "Greg Traweek",
            "description": "Trinity USA",
            "street1": "227 Marketridge Dr",
            "street2": null,
            "street3": null,
            "city": "Ridgeland",
            "state": "MS",
            "zip": "39157",
            "country": "USA",
            "phone": "601-713-2628"
        }
    },
    {
        "id": 843257,
        "title": "TEST-843257",
        "order_id": 385194,
        "copied_garment_id": null,
        "garment_type": "CTOPC",
        "prefix": "TEST",
        "index": "",
        "created_at": "2018-04-19T18:14:30.000Z",
        "updated_at": null,
        "last_status_change_date": "2018-04-19T18:14:30.000Z",
        "last_delay_change_date": null,
        "links": {
            "gerber": "http://localhost:8080/share/order_insert.php?suit_ids[]=843257&units=uscust&format=gerber&fabtype=both",
            "order_insert": "https://trinity-apparel.com/share/order_insert.php?format=pdfzip&units=si&suit_ids%5B%5D=843257",
            "order_split": "https://documents.trinity-apparel.com/order_splits?garment_id=843257&locale=en"
        },
        "manufacturer": {
            "id": 5,
            "name": "Trisco TAM",
            "email": "info@trinity-apparel.com"
        },
        "fabric": {
            "id": 41888,
            "active": true,
            "in_stock": 1,
            "restock_date": null,
            "description": "Blue Navy Twill",
            "supplier_fabric_number": "BT65153-11",
            "trinity_fabric_number": "C4-3441888",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/C4-3441888",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=C4-3441888&res=300",
            "inventory_status": "In Stock",
            "pattern_id": null,
            "weave_id": 7,
            "price_tier": 1,
            "discount": null,
            "has_image": true,
            "availability": "at once",
            "favorite_id": null,
            "fabric_type": null,
            "fabric_garment_type": 231,
            "trim_garment_type": 0
        },
        "order_status": {
            "code": "READY",
            "name": "Pending",
            "description": "Ready"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 385194,
            "title": "DO-385194",
            "custom_order_number": "",
            "garment_count": 0,
            "ship_type": "Ground",
            "measurement_units": "uscust",
            "ordered_at": null,
            "created_at": "2018-04-18T12:28:50.000Z",
            "invoiced_at": null
        },
        "outgoing_address": {
            "id": 1,
            "description": "Trinity USA",
            "street1": "227 Marketridge Dr",
            "street2": null,
            "street3": null,
            "city": "Ridgeland",
            "state": "MS",
            "zip": "39157",
            "country": "USA",
            "phone": "601-713-2628"
        }
    },
    ...
]
```

Returns an array of garments that are ready for download.

Right after a customer places an order, Trinity validates the order and requests materials if needed. Once the order is validated and fabric is received, it moves out of a hold status and is ready for download. These garments are in `Ready` status and have no delay status.

We expect the manufacturer to get a list of garments, then get garment details, fabric, options and measurements info. Once this is obtained, they will move the order status to `Blue Pencil`, which means that the factory downloaded the order and is laying the marker and putting the order into the production plan. When those tasks are completed the order moves to `Cutting` and then to `Production`.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/download_garments`

### Query Parameters

| Parameter       | Default | Description                                                                                                |
| --------------- | ------- | ---------------------------------------------------------------------------------------------------------- |
| garment_id      | N/A     | Filter the list to a specific garment_id or list of garment_ids (using `garment_id[]=` array style syntax) |
| manufacturer_id | N/A     | If set, returns only garments from a specific manufacturer id                                              |

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: Yes

### Examples

#### Download from a specific manufacturer

`GET https://api.trinity-apparel.com/v1/download_garments?manufacturer_id=4`

Returns garments from a specific factory

#### Download specific garments

`GET https://api.trinity-apparel.com/v1/download_garments?garment_id[]=1001234&garment_id[]=1002345&garment_id[]=1003456`

Returns garments #1001234, #1002345, and #1003456 as long as they are in `Ready` status and have no delays.

## Garment Properties

```shell
curl "https://api.trinity-apparel.com/v1/garments/:id/properties"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
  "measurements": [
{
      "id": 2,
      "name": "height",
      "description": "Height",
      "value": 182.88,
      "last_modified": "2019-06-27 14:05:57 UTC",
      "garment_type": 7,
      "garment_types": [
        "csc",
        "cv",
        "ct"
      ],
      "units": "cm"
    },
    {
      "id": 3,
      "name": "weight",
      "description": "Weight",
      "value": 78.46,
      "last_modified": "2019-06-27 14:05:57 UTC",
      "garment_type": 7,
      "garment_types": [
        "csc",
        "cv",
        "ct"
      ],
      "units": "kgs"
    },
    {
      "id": 6,
      "name": "coat_fit",
      "description": "Coat Fit",
      "value": "trim",
      "last_modified": "2019-06-27 14:05:57 UTC",
      "garment_type": 1,
      "garment_types": [
        "csc"
      ]
    },

    ...

    {
      "id": 276,
      "name": "round_back",
      "description": "Round Back",
      "value": "",
      "last_modified": "2019-06-27 14:05:57 UTC",
      "garment_type": 1,
      "garment_types": [
        "csc"
      ]
    },
    {
      "id": 289,
      "name": "lower_back_crotch",
      "description": "Lower Back Crotch",
      "value": "normal",
      "last_modified": "2019-06-27 14:05:57 UTC",
      "garment_type": 4,
      "garment_types": [
        "ct"
      ]
    }
  ],
  "options": [
{
      "option": {
        "id": 1,
        "name": "garment_label",
        "description": "Garment Label"
      },
      "option_value": {
        "id": 374,
        "value": "dealer_label",
        "description": "用客供商标"
      },
      "garment_type": 1,
      "garment_types": [
        "csc"
      ]
    },
    {
      "option": {
        "id": 2,
        "name": "vent_style",
        "description": "Vent Style"
      },
      "option_value": {
        "id": 7,
        "value": "side_vent",
        "description": "双开衩-标准24cm"
      },
      "garment_type": 1,
      "garment_types": [
        "csc"
      ]
    },
    {
      "option": {
        "id": 3,
        "name": "shoulder_style",
        "description": "Shoulder Style"
      },
      "option_value": {
        "id": 656,
        "value": "ultra_soft",
        "description": "超薄休闲肩"
      },
      "garment_type": 1,
      "garment_types": [
        "csc"
      ]
    },

    ...

    {
      "option": {
        "id": 234,
        "name": "formal_treatment_waistband",
        "description": "Formal Treatment Position - Waistband"
      },
      "option_value": {
        "id": 1503,
        "value": "no",
        "description": "绸缎腰面 - 无"
      },
      "garment_type": 4,
      "garment_types": [
        "ct"
      ]
    },

    ...

    {
      "option": {
        "id": 611,
        "name": "bottom_style",
        "description": "Bottom Style"
      },
      "option_value": {
        "id": 10645,
        "value": "pointed",
        "description": ""
      },
      "garment_type": 2,
      "garment_types": [
        "cv"
      ]
    }
  ],

  "materials": {
    "fabrics": [
      {
        "id": 73096,
        "name": "K4-3973096",
        "description": "Black Fancy Solid",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/K4-3973096",
        "options": [
          {
            "id": null,
            "name": "shell",
            "description": "Shell Fabric",
            "garment_type": 5,
            "garment_types": [
              "csc",
              "ct"
            ]
          }
        ],
        "usage": "shell",
        "trinity_number": "K4-3973096",
        "supplier_number": "C21125-01",
        "quantity": {
          "cad": {
            "width": null,
            "length": null,
            "is_cut": null
          },
          "received": {
            "width": null,
            "length": null,
            "notes": null
          },
          "repeated_pattern": {
            "width": null,
            "length": null,
            "type": null
          }
        }
      },
      ...
    ],
      ...
    "buttons": [
      {
        "id": 2,
        "name": "KYKW024_Cinnamon",
        "description": "2-11 Cinnamon Marbled Premium",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-11_Cinnamon_Marbled_Premium?wid=100",
        "options": [
          {
            "id": 21,
            "name": "button_color",
            "description": "Button Color/Type",
            "garment_type": 1,
            "garment_types": [
              "csc"
            ]
          },
          {
            "id": 244,
            "name": "button_color",
            "description": "Button Color/Type",
            "garment_type": 4,
            "garment_types": [
              "ct"
            ]
          },
          {
            "id": 290,
            "name": "button_color",
            "description": "Button Color/Type",
            "garment_type": 2,
            "garment_types": [
              "cv"
            ]
          },
          {
            "id": 507,
            "name": "materials_button_color",
            "description": "Button Color",
            "garment_type": 1,
            "garment_types": [
              "csc"
            ]
          },
          {
            "id": 512,
            "name": "materials_button_color",
            "description": "Button Color/Type",
            "garment_type": 2,
            "garment_types": [
              "cv"
            ]
          },
          {
            "id": 516,
            "name": "materials_button_color",
            "description": "Button Color/Type",
            "garment_type": 4,
            "garment_types": [
              "ct"
            ]
          }
        ],
        "quantity": {
          "32L": {
            "csc": 3
          },
          "24L": {
            "csc": 16,
            "cv": 8,
            "ct": 3
          }
        }
      }
    ],
    "threads": [
      {
        "id": 27,
        "name": "silver",
        "description": "Silver",
        "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=231,231,231&fmt=png-alpha",
        "options": [
          {
            "id": 225,
            "name": "pic_stitching_lining_edge",
            "description": "Pic Stitching - Lining Edge",
            "garment_type": 1,
            "garment_types": [
              "csc"
            ]
          },
          ...
        ]
      }
    ],
    "suedes": [],
    "labels": [
      {
        "id": 11,
        "name": "direct_embroider_lining",
        "description": "Embroider Directly on Garment Lining",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/Embroidery_Lining?wid=300",
        "options": [
          {
            "id": 84,
            "name": "customer_label",
            "description": "Coat Name Label",
            "garment_type": 1,
            "garment_types": [
              "csc"
            ]
          }
        ]
      },
      ...
    ],
    "pocket_bags": [
      {
        "id": null,
        "name": "front_pocket_l",
        "description": "Default Front Left Pocket Bag",
        "image": null,
        "options": [
          {
            "id": null,
            "name": "front_pockets",
            "description": "front_pockets",
            "garment_type": 4,
            "garment_types": [
              "ct"
            ]
          }
        ],
        "quantity": {
          "length": 14.57,
          "width": 7.87
        }
      },
      ...
    ],
    "dealer_labels": [
      {
        "id": "TAGDL-0264",
        "name": "Well Suited Custom Clothiers 813-545-2700",
        "description": "[\"7.9\", \"4\"]",
        "image": "https://workflow.trinity-apparel.com/images/labels/TAGDL-0264.jpg",
        "options": [
          {
            "id": 1,
            "name": "garment_label",
            "description": "Garment Label",
            "garment_type": 1,
            "garment_types": [
              "csc"
            ]
          }
        ],
        "quantity": 1,
        "dealer_id": 952,
        "size": {
          "width": "7.9",
          "length": "4"
        }
      }
    ]
  }
}
```

Returns an array of `measurements`, an array of `options`, and a hash of `materials`. The materials hash includes `fabrics`, `buttons`, `threads`, `labels`, `suedes`, `felts`, `pocket_bags`, and `dealer_labels`, each of which contains an array of those type of materials.

### How it Works

All measurements are flat objects that include the measurement name and value. We also include the description and last modified date, as well as the numeric garment type and an array of all garment types the measurement is valid used in this garment (E.g., height would be valid for each piece in a suit). When the measurement value is numeric, we convert it into the appropriate measurement units for the factory (typically SI) and list the units. Measurements are also adjusted to be finished. Synthetic measurements (measurements that the dealer did not enter) are calculated and inserted into this list.

All options include the option and option value. The option includes the id, name, and english description (there's no translation for the option). The option value includes the id, value, and a localized description (translated for the appropriate garment manufacturer for the order). We use the translation if available, if not we fallback to English. We also include the garment type (numeric bitmask) and an array of valid garment types (abbreviations). Synthetic options (not entered by the dealer) may also be inserted into the options list.

In addition to options, we also provide a list of all materials needed to make the garment. Materials include fabrics, buttons, threads, labels, suedes, felts, pocket bags, and dealer labels. We include information specific to that material type (Trinity fabric number, thread code, etc), id, name, description, and image, which is a web link that you can use to display the material. Fabrics have a usage field, which can be shell (main fabric), lining, trim, or other. We also include a list of all options that use this material.

We also include the quantity of each particular button under the `quantity` field. The quantity includes a number for small and large buttons. If the quantity is null, then we were unable to calculate the button count for that particular button.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/garments/:id/properties`

### Query Parameters

| Parameter | Default | Description                                  |
| --------- | ------- | -------------------------------------------- |
| id        | N/A     | The specific garment you want information on |

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: No

### Future Plans

We plan to provide quantities (measurements or counts) of all materials.
We can also add filters and allow users to toggle localization (metric units, translations) if that is important.

## Garment Properties - Materials

Garment properties includes custom objects in the `materials` hash. The materials object includes: fabrics, buttons, threads, suedes, felts, labels, pocket bags, and dealer labels.

### Materials Fabrics

```json
# Materials fabric object
{
  "id": 70218,
  "name": "TT-3970218",
  "description": "Lt Gray Solid",
  "image": "https://s7d4.scene7.com/is/image/trinityapparel/TT-3970218",
  "options": [
    {
      "id": null,
      "name": "shell",
      "description": "Shell Fabric",
      "garment_type": 5,
      "garment_types": [
        "csc",
        "ct"
      ]
    }
  ],
  "trinity_number": "TT-3970218",
  "supplier_number": "GV100-10",
  "quantity": {
    "cad": {
      "width": null,
      "length": null,
      "is_cut": null
    },
    "received": {
      "width": null,
      "length": null,
      "notes": null
    },
    "repeated_pattern": {
      "width": null,
      "length": null,
      "type": null
    }
  }
}
```

Array of unique fabrics used in the garment.

| Attribute                                       | Description                                                     |
| ----------------------------------------------- | --------------------------------------------------------------- |
| id <br> <span>integer</span>                    | Unique identifier for the fabric.                               |
| name <br> <span>string</span>                   | Trinity Fabric Number                                           |
| description <br> <span>string</span>            | Text describing the colors and pattern of the fabric            |
| image <br> <span>string</span>                  | Full url to an image of the fabric.                             |
| supplier_fabric_number <br> <span>string</span> | A unique identifier / SKU according to the fabric supplier      |
| trinity_fabric_number <br> <span>string</span>  | A unique identifier / SKU according to Trinity                  |
| options <br> <span>subresource</span>           | List of options that the fabric is used in (shell is an option) |
| quantity <br> <span>subresource</span>          | An array of measurements for the fabric                         |

#### Quantity Subresource

CAD

Length and width determined by processing the order in Gerber

| Attribute                        | Description              |
| -------------------------------- | ------------------------ |
| length <br> <span>float</span>   | Length in centimeters    |
| width <br> <span>float</span>    | Width in centimeters     |
| is_cut <br> <span>boolean</span> | Has the fabric been cut? |

Received

Length and width are measured when a single length of fabric is received. Does not apply to fabrics that are in factory inventory.

| Attribute                      | Description                                     |
| ------------------------------ | ----------------------------------------------- |
| length <br> <span>float</span> | Length in centimeters                           |
| width <br> <span>float</span>  | Width in centimeters                            |
| notes <br> <span>string</span> | (optional) Notes about fabric that was received |

Repeated Pattern

Length and width of the pattern (stripe, plaid, etc) when a fabric is received. Does not apply to fabrics that are in factory inventory. Does not apply to solids.

| Attribute                      | Description                                                                         |
| ------------------------------ | ----------------------------------------------------------------------------------- |
| length <br> <span>float</span> | Length in centimeters                                                               |
| width <br> <span>float</span>  | Width in centimeters                                                                |
| type <br> <span>string</span>  | Types are: Solid/Paisley, Stripes, 'Check 1 - Symmetric' and 'Check 2 - Asymmetric' |

### Materials Buttons

```json
# Material Button object
{
  "id": 244,
  "name": "JD1692-D181_Medium_Gray",
  "description": "1-03 Medium Gray",
  "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-03_Medium_Gray?wid=100",
  "options": [
    {
      "id": 208,
      "name": "sleeve_button_color",
      "description": "Sleeve Button Color",
      "garment_type": 1,
      "garment_types": [
        "csc"
      ]
    },
    ...
  ],
  "quantity": {
    "24L": {
      "csc": 9,
      "ct": 0
    },
    "32L": {
      "csc": 3,
      "ct": 0
    }
  }
}
```

Array of unique buttons used in the garment

| Attribute                              | Description                                    |
| -------------------------------------- | ---------------------------------------------- |
| id <br> <span>integer</span>           | Unique identifier for the button.              |
| name <br> <span>string</span>          | Supplier Number                                |
| description <br> <span>string</span>   | Description of button used in ordering system. |
| image <br> <span>string</span>         | Full url to an image of the button.            |
| options <br> <span>subresource</span>  | List of options that the button is used in.    |
| quantity <br> <span>subresource</span> | An array of button counts for the garment      |

We separate each button size by using the Ligne scale. Inside each button size, we list the button count needed by garment type (E.g., csc for jacket).

### Materials Threads

```json
# Material Thread object
{
  "id": 1,
  "name": "black",
  "description": "Black",
  "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=27,27,27&fmt=png-alpha",
  "options": [
    {
      "id": 262,
      "name": "waistband_color",
      "description": "Waistband Fabric",
      "garment_type": 4,
      "garment_types": [
        "ct"
      ]
    }
  ]
}
```

Array of unique threads used in the garment

| Attribute                             | Description                                    |
| ------------------------------------- | ---------------------------------------------- |
| id <br> <span>integer</span>          | Unique identifier for the thread.              |
| name <br> <span>string</span>         | Supplier Number                                |
| description <br> <span>string</span>  | Description of thread used in ordering system. |
| image <br> <span>string</span>        | Full url to an image of the thread.            |
| options <br> <span>subresource</span> | List of options that the thread is used in.    |

### Materials Suedes

```json
{
  "id": 3,
  "name": "MS-219185_charcoal",
  "description": "7-04 Charcoal",
  "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-04_Charcoal?&hei=100",
  "options": [
    {
      "id": 447,
      "name": "microsuede_undercollar_color",
      "description": "Microsuede Undercollar",
      "garment_type": 1,
      "garment_types": ["csc"]
    }
  ]
}
```

Array of unique suedes used in the garment

| Attribute                             | Description                                   |
| ------------------------------------- | --------------------------------------------- |
| id <br> <span>integer</span>          | Unique identifier for the suede.              |
| name <br> <span>string</span>         | Supplier Number                               |
| description <br> <span>string</span>  | Description of suede used in ordering system. |
| image <br> <span>string</span>        | Full url to an image of the suede.            |
| options <br> <span>subresource</span> | List of options that the suede is used in.    |

### Materials Labels

```json
{
  "id": 15,
  "name": "light_gray_label",
  "description": "Light Gray Label",
  "image": "http://s7d4.scene7.com/is/image/trinityapparel/light_grey_label?wid=300",
  "options": [
    {
      "id": 84,
      "name": "customer_label",
      "description": "Coat Name Label",
      "garment_type": 1,
      "garment_types": ["csc"]
    }
  ]
}
```

Array of unique labels used in the garment

| Attribute                             | Description                                   |
| ------------------------------------- | --------------------------------------------- |
| id <br> <span>integer</span>          | Unique identifier for the label.              |
| name <br> <span>string</span>         | Unique string for label                       |
| description <br> <span>string</span>  | Description of label used in ordering system. |
| image <br> <span>string</span>        | Full url to an image of the label.            |
| options <br> <span>subresource</span> | List of options that the label is used in.    |

### Materials Felts

```json
# Material Felt object
{
  "id": 21,
  "name": "FLD-0630_light_gray",
  "description": "6-03 Light Gray",
  "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-03_Light_Gray?&hei=100",
  "options": [
    {
      "id": 446,
      "name": "felt_undercollar_color",
      "description": "Felt Undercollar",
      "garment_type": 1,
      "garment_types": [
        "csc"
      ]
    }
  ]
}
```

Array of unique felts used in the garment

| Attribute                             | Description                                  |
| ------------------------------------- | -------------------------------------------- |
| id <br> <span>integer</span>          | Unique identifier for the felt.              |
| name <br> <span>string</span>         | Supplier Number                              |
| description <br> <span>string</span>  | Description of felt used in ordering system. |
| image <br> <span>string</span>        | Full url to an image of the felt.            |
| options <br> <span>subresource</span> | List of options that the felt is used in.    |

### Materials Pocket Bags

```json
# Material Pocket Bag object
{
  "id": null,
  "name": "front_pocket_l",
  "description": "Default Front Left Pocket Bag",
  "image": null,
  "options": [
    {
      "id": null,
      "name": "front_pockets",
      "description": "front_pockets",
      "garment_type": 4,
      "garment_types": [
        "ct"
      ]
    }
  ],
  "quantity": {
    "length": 14.57,
    "width": 7.87
  }
}
```

Array of pocket bags needed in the garment

| Attribute                              | Description                                                  |
| -------------------------------------- | ------------------------------------------------------------ |
| id <br> <span>integer</span>           | Not set                                                      |
| name <br> <span>string</span>          | Location of the pocket bag                                   |
| description <br> <span>string</span>   | Verbose description of the pocket bag (based on pocket type) |
| image <br> <span>string</span>         | Not set                                                      |
| options <br> <span>subresource</span>  | List of options that the felt is used in.                    |
| quantity <br> <span>subresource</span> | Length and width of the bag in inches.                       |

There are currently four locations for pocket bags:

- front_pocket_l
- front_pocket_r
- back_pocket_l
- back_pocket_r

Some garments will not have back pockets, so there will not always be four pocket bags in the array.

### Materials Dealer Labels

```json
# Material Dealer Label object
{
    "id": "TAGDL-0264",
    "name": "Well Suited Custom Clothiers 813-545-2700",
    "description": "[\"7.9\", \"4\"]",
    "image": "https://workflow.trinity-apparel.com/images/labels/TAGDL-0264.jpg",
    "options": [
      {
        "id": 1,
        "name": "garment_label",
        "description": "Garment Label",
        "garment_type": 1,
        "garment_types": [
          "csc"
        ]
      }
    ],
    "quantity": 1,
    "dealer_id": 952,
    "size": {
      "width": "7.9",
      "length": "4"
    }
}
```

Array of unique felts used in the garment

| Attribute                             | Description                                                 |
| ------------------------------------- | ----------------------------------------------------------- |
| id <br> <span>string</span>           | Unique SKU for the dealer label. Used for Trinity inventory |
| name <br> <span>string</span>         | Dealer Name                                                 |
| description <br> <span>string</span>  | Usually the size in centimeters: [length, width]            |
| image <br> <span>string</span>        | Full url to an image of the dealer label.                   |
| options <br> <span>subresource</span> | List of options that the dealer label is used in.           |
| quantity <br> <span>integer</span>    | Number of labels needed to make the garment                 |
| dealer_id <br> <span>integer</span>   | Trinity Dealer ID - unique per dealer                       |
| size <br> <span>subresource</span>    | length and width are extracted from the description field   |

## Get All Embroidery

```shell
curl "https://api.trinity-apparel.com/v1/embroidery"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "garment": {
            "id": 1079766,
            "manufacturer_id": 4,
            "garment_type": 5,
            "created_at": "2019-10-30T09:32:14.000Z"
        },
        "option": {
            "id": 89,
            "name": "customer_label_text",
            "garment_type": 1,
            "garment_types": [
                "csc"
            ]
        },
        "text": "J WHITE",
        "font": "Copper Plate",
        "color": "5-06 Charcoal",
        "position": "T4 - Left Below Breast Pkt",
        "size": null
    },
    {
        "garment": {
            "id": 1079773,
            "manufacturer_id": 4,
            "garment_type": 5,
            "created_at": "2019-10-30T09:43:50.000Z"
        },
        "option": {
            "id": 89,
            "name": "customer_label_text",
            "garment_type": 1,
            "garment_types": [
                "csc"
            ]
        },
        "text": "MWJ",
        "font": "Calligraphy",
        "color": "5-65 Dark Olive",
        "position": "Undercollar Position",
        "size": null
    },
    {
        "garment": {
            "id": 1079774,
            "manufacturer_id": 4,
            "garment_type": 5,
            "created_at": "2019-10-30T09:45:37.000Z"
        },
        "option": {
            "id": 89,
            "name": "customer_label_text",
            "garment_type": 1,
            "garment_types": [
                "csc"
            ]
        },
        "text": "John Eden",
        "font": "Calligraphy",
        "color": "5-54 Gold",
        "position": "T2 - Left Above Breast Pkt",
        "size": null
    },
    {
        "garment": {
            "id": 1079782,
            "manufacturer_id": 4,
            "garment_type": 32,
            "created_at": "2019-10-30T09:58:27.000Z"
        },
        "option": {
            "id": 89,
            "name": "customer_label_text",
            "garment_type": 32,
            "garment_types": [
                "ctopc"
            ]
        },
        "text": "HEPPERMANN",
        "font": "Copper Plate",
        "color": "5-03 Light Gray",
        "position": "T4 - Left Below Breast Pkt",
        "size": null
    },
    ...
]
```

Returns an array of embroidery objects. There can be more than one embroidery per garment. The object includes minimal objects for garment and fabric, plus flattened option values for text, font, color, position and size of the embroidery. The list is ordered by when the garments were created.

[Click here](#embroidery) for details on the response objects.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/embroidery`

### Query Parameters

| Parameter         | Default | Description                                                                  |
| ----------------- | ------- | ---------------------------------------------------------------------------- |
| garment_id        | N/A     | One or more garment ids. Use array style syntax `garment_id[]` for multiple. |
| start_date        | N/A     | Start of date range. Must be ISO-8601 date (YYYY-MM-DD)                      |
| end_date          | N/A     | End of date range. Must be ISO-8601 date (YYYY-MM-DD)                        |
| order_status_code | N/A     | Filter using a single [order status](#order-statuses)                        |

A garment id, list of garment ids, or a date range (start and end date) must be provided.

_NOTE_: If specific garment(s) are not provided AND an order status is not provided, we filter by production statuses: STATUS_READY, STATUS_BLUE_PENCIL, STATUS_CUTTING, STATUS_PRODUCTION

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: No

### Examples

#### Embroidery for multiple garments

`GET https://api.trinity-apparel.com/v1/embroidery?garment_id[]=1001234&garment_id[]=1002345&garment_id[]=1003456`

Returns garments #1001234, #1002345, and #1003456

#### Embroidery for garments ordered on a specific day

`GET https://api.trinity-apparel.com/v1/embroidery?start_date=2019-10-30&end_date=2019-10-30`

Returns garments ordered on a specific day, October 30th.

#### Embroidery for garments ordered on a specific day and order status

`GET https://api.trinity-apparel.com/v1/embroidery?start_date=2019-10-30&end_date=2019-10-30&order_status_code=PREP`

Returns garments in Blue Pencil (code = PREP) status that were ordered on a specific day, October 30th.

## Get Specific Embroidery

```shell
curl "https://api.trinity-apparel.com/v1/garments/:id/embroidery"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
  {
    "garment": {
      "id": 1081783,
      "manufacturer_id": 4,
      "garment_type": 1,
      "created_at": "2019-11-03T18:47:22.000Z"
    },
    "option": {
      "id": 89,
      "name": "customer_label_text",
      "garment_type": 1,
      "garment_types": ["csc"]
    },
    "text": "M Kiser",
    "font": "Calligraphy",
    "color": "5-01 White",
    "position": "T4 - Left Below Breast Pkt",
    "size": null
  }
]
```

Returns an array of embroidery objects. There can be more than one embroidery per garment. The object includes minimal objects for garment and fabric, plus flattened option values for text, font, color, position and size of the embroidery.

[Click here](#embroidery) for details on the response objects.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/garments/:id/fabrics`

### Query Parameters

| Parameter | Default | Description                               |
| --------- | ------- | ----------------------------------------- |
| id        | N/A     | The specific garment you want fabrics for |

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: No

## Update Fabric

```shell
curl -X POST "https://api.trinity-apparel.com/v1/fabrics/:id"
  -H "Authorization Bearer: swaledale"
```

> The above command returns a `202 Accepted` and no JSON output when it is successful.

### Description

This call updates a fabric. Manufacturers will regularly update fabric attributes when a fabric is received.

### Rules

All non-CMT fabrics can be modified.

Pattern Measurement rules:

- Solids cannot have pattern width or pattern offset. Must be set to null or ""
- Stripes must have pattern width
- Checks (symmetric and asymmetric) must have pattern width and length
- You must provide pattern measurements when setting the pattern_type

### HTTP Request

`GET https://api.trinity-apparel.com/v1/fabrics/:id`

### Query Parameters

| Parameter                 | Default | Description                                                                                                                              |
| ------------------------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| id                        | N/A     | id number for the fabric                                                                                                                 |
| fabric_weight_grams_meter | N/A     | Weight of a meter of fabric, in grams                                                                                                    |
| cuttable_width            | N/A     | Cuttable Width in inches (in)                                                                                                            |
| pattern_type              | N/A     | `solid`, `stripe`, `check_symmetric`, or `check_asymmetric`                                                                              |
| pattern_width             | N/A     | Width of the repeated pattern in inches (in)                                                                                             |
| width_offset              | N/A     | optional. Widthwize offset of the repeated pattern in inches (in)                                                                        |
| pattern_length            | N/A     | Length of the repeated pattern in inches (in)                                                                                            |
| length_offset             | N/A     | optional. Lengthwise Offset of the repeated pattern in inches (in)                                                                       |
| grain_repeat              | N/A     | boolean; Are there lines parallel to the grain that repeat?                                                                              |
| crosswise_repeat          | N/A     | boolean; Are there lines perpindicular to the grain that repeat?                                                                         |
| one_way_nap               | N/A     | boolean; Does the fabric appear different from one side? Affects corduroys and velvets. Marker pieces can't be mirrored on a one way nap |
| horiz_pattern             | N/A     | boolean; Is the repeat naturally horizontal?                                                                                             |
| non_iron                  | N/A     | boolean; True if the fabric cannot be ironed.                                                                                            |

- Any measurement field can be reset by making an api call with a blank parameter (eg., `&pattern_width=`)

### Other

- Permissions: Only manufacturers can access this route.
- Pagination: N/A

### Responses

| Response Code | Description                                          |
| ------------- | ---------------------------------------------------- |
| 201           | Fabric was successfully changed                      |
| 403           | Not Authorized - You're not a factory                |
| 409           | Unable to update the fabric. Reason provided in JSON |

## Create Fabric Cut

```shell
curl -X POST "https://api.trinity-apparel.com/v1/fabric_cuts"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
  "id": 546845,
  "is_cut": false,
  "created_at": "2019-11-14T22:09:36.000Z",
  "length": 1342,
  "actual_length": 1337,
  "width": 13,
  "garment": {
    "id": 1004082,
    "title": "ID-1004082",
    "created_at": "2019-04-30T17:23:39.000Z",
    "garment_type": "CSC"
  },
  "fabric": {
    "id": 54926,
    "description": "Grey Charcoal Twill",
    "trinity_fabric_number": "C4-3754926",
    "url": "https://s7d4.scene7.com/is/image/trinityapparel/C4-3754926",
    "has_image": true
  },
  "option": null
}
```

### Description

This call tracks the fabric cuts (CAD lengths) of fabrics. Cut lengths for all shell, lining, and a few specific options for each garment need to be entered into the Trinity system.

### Rules

If cut lengths are provided for all fabrics, then that garment will automatically move to CUTTING status.

### HTTP Request

`POST https://api.trinity-apparel.com/v1/fabric_cuts`

### Query Parameters

| Parameter | Default | Description                             |
| --------- | ------- | --------------------------------------- |
| id        | N/A     | Garment ID                              |
| fabric_id | N/A     | Fabric ID. Integer not String           |
| length_m  | N/A     | Fabric length in centimeters            |
| width_m   | N/A     | Fabric width in centimeters             |
| is_cut    | false   | Boolean. Denotes if fabric has been cut |

### Other

- Permissions: Only manufacturers can access this route. They can only modify garments made at their factory.
- Pagination: N/A

### Responses

| Response Code | Description                                                                         |
| ------------- | ----------------------------------------------------------------------------------- |
| 201           | Fabric cut entry was created                                                        |
| 403           | Error: Not Authorized - You're not a factory or the garment isn't from your factory |
| 409           | Error: Unable to create a fabric cut. Error message is provided                     |

## Get All Fabric Cuts

```shell
curl "https://api.trinity-apparel.com/v1/fabric_cuts"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 546530,
        "is_cut": false,
        "created_at": "2019-11-07T03:23:42.000Z",
        "length": 475,
        "actual_length": 470,
        "width": 1,
        "garment": {
            "id": 1015730,
            "title": "IDUK-1015730",
            "created_at": "2019-05-28T12:25:00.000Z",
            "garment_type": "CCP"
        },
        "fabric": {
            "id": 61257,
            "description": "Char Blue Wine Plaid",
            "trinity_fabric_number": "K4-3861257",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/K4-3861257",
            "has_image": true
        },
        "option": null
    },
    {
        "id": 546531,
        "is_cut": false,
        "created_at": "2019-11-07T03:23:42.000Z",
        "length": 165,
        "actual_length": 160,
        "width": 146,
        "garment": {
            "id": 1015730,
            "title": "IDUK-1015730",
            "created_at": "2019-05-28T12:25:00.000Z",
            "garment_type": "CCP"
        },
        "fabric": {
            "id": 40512,
            "description": "Burgundy Camouflage",
            "trinity_fabric_number": "L2-3540512",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/L2-3540512",
            "has_image": true
        },
        "option": {
            "id": 229,
            "name": "lining_fabric_num",
            "description": "Lining Fabric #"
        }
    },
    {
        "id": 546307,
        "is_cut": false,
        "created_at": "2019-11-07T01:58:49.000Z",
        "length": 455,
        "actual_length": 450,
        "width": 148,
        "garment": {
            "id": 1068322,
            "title": "ID-1068322",
            "created_at": "2019-10-04T00:14:08.000Z",
            "garment_type": "CCVP"
        },
        "fabric": {
            "id": 42243,
            "description": "Black Pinstripe",
            "trinity_fabric_number": "LA-3542243",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/LA-3542243",
            "has_image": true
        },
        "option": null
    },
    {
        "id": 546308,
        "is_cut": false,
        "created_at": "2019-11-07T01:58:49.000Z",
        "length": 390,
        "actual_length": 385,
        "width": 136,
        "garment": {
            "id": 1068322,
            "title": "ID-1068322",
            "created_at": "2019-10-04T00:14:08.000Z",
            "garment_type": "CCVP"
        },
        "fabric": {
            "id": 27476,
            "description": "Black Skulls",
            "trinity_fabric_number": "L6-3127476",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/L6-3127476",
            "has_image": true
        },
        "option": {
            "id": 229,
            "name": "lining_fabric_num",
            "description": "Lining Fabric #"
        }
    },
    ...
]
```

Returns an array of fabric cuts.

[Click here](#fabric-cuts) for details on the response objects.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/fabric_cuts`

### Query Parameters

| Parameter         | Default   | Description                                                                                             |
| ----------------- | --------- | ------------------------------------------------------------------------------------------------------- |
| manufacturer_id   | N/A       | Manufacturer ID for the factory                                                                         |
| garment_id        | N/A       | One or more garment ids. Use array style syntax `garment_id[]` for multiple.                            |
| fabric_id         | N/A       | One or more fabric ids. Use array style syntax `fabric_id[]` for multiple.                              |
| is_cut            | false     | Filter by if the fabric has been cut                                                                    |
| order_status_code | Read more | Optional. Default is `BLUE_PENCIL` and `CUTTING`. Filter using a single [order status](#order-statuses) |

A manufacturer_id must be provided.

_NOTE_: If order status is not provided, we filter by these statuses: STATUS_BLUE_PENCIL and STATUS_CUTTING

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: Yes, but 1000 at a time

### Examples

#### Fabric cuts for one factory

`GET https://api.trinity-apparel.com/v1/fabric_cuts?manufacturer_id=2`

Returns all fabric cuts from manufacturer 2 that are from garments in CUTTING OR BLUE PENCIL status..

#### Fabric cuts for 3 specific garments

`GET https://api.trinity-apparel.com/v1/fabric_cuts?garment_id[]=1001234&garment_id[]=1002345&garment_id[]=1003456`

Returns all fabric cuts that came for 3 specific garments.

#### Fabric cuts for a specific fabric that are in an order status

`GET https://api.trinity-apparel.com/v1/fabric_cuts?fabric_id=50505&order_status_code=READY`

Returns all fabric cuts for garments in Ready (code = READ) status that use a particular fabric.

## Update Fabric Cut

```shell
curl -X POST "https://api.trinity-apparel.com/v1/fabric_cuts/:id"
  -H "Authorization Bearer: swaledale"
```

> The above command returns a `202 Accepted` and no JSON output when it is successful.

### Description

This call updates a fabric cut. Users can only modify the `is_cut` boolean and set it to true or false.

### Rules

The fabric cut may only be modified while the garment is in a production status: `BLUE_PENCIL`, `CUTTING`, `READY`, or `PRODUCTION`.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/fabric_cuts/:id`

### Query Parameters

| Parameter | Default | Description           |
| --------- | ------- | --------------------- |
| id        | N/A     | id number for the cut |

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: N/A

### Responses

| Response Code | Description                                                              |
| ------------- | ------------------------------------------------------------------------ |
| 201           | Fabric cut was successfully changed                                      |
| 403           | Not Authorized - You're not a factory or the cut isn't from your factory |
| 409           | Unable to update the fabric cut. Reason provided in JSON                 |

## Set Order Status

```shell
curl -X POST "https://api.trinity-apparel.com/v1/garments/:id/order_statuses/:order_status"
  -H "Authorization Bearer: swaledale"
```

> The above command returns a `201 Created` and no JSON output when it is successful.

### Description

This call updates the order status of a garment and puts an entry in garment history to note when the change was made.

Our customers, partners, and staff can see the order status for each garment. It helps us set expecations for when we can make delivery, so it is important to keep things up to date.

### Rules

Trinity enforces strict validation rules so that garments can only move to a few order statuses from any given status. Here are the valid transitions for each status:

| Starting Status       | Valid Destination Status                                      |
| --------------------- | ------------------------------------------------------------- |
| Incomplete            | CMT Fabric Hold, Fabric Hold, Ready, Cancelled                |
| CMT Fabric Hold       | Fabric Hold, Ready, Cancelled                                 |
| Fabric Hold           | Ready, Cancelled                                              |
| Ready                 | Blue Pencil, Cutting, Production, Cancelled                   |
| Blue Pencil           | Cutting, Production, Production Complete, Cancelled           |
| Cutting               | Production, Production Complete, Cancelled                    |
| Production            | Production Complete, International Transit, Cancelled         |
| Production Complete   | International Transit, Direct Ship, Cancelled                 |
| International Transit | Final Inspection, Shipment Processing, Direct Ship, Cancelled |
| Final Inspection      | Shipment Processing, Delivery, Direct Ship, Cancelled         |
| Shipment Processing   | Delivery, Direct Ship, Cancelled                              |
| Delivery              | Shipment Processing, Cancelled                                |
| Direct Ship           | Production Complete, Cancelled                                |
| Cancelled             |                                                               |

### HTTP Request

`GET https://api.trinity-apparel.com/v1/garments/:id/order_statuses/:order_status`

### Query Parameters

| Parameter    | Default | Description                                                                |
| ------------ | ------- | -------------------------------------------------------------------------- |
| order_status | N/A     | Can be an id number or a code. [Click here](#order-statuses) for more info |

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: N/A

### Responses

| Response Code | Description                                                                  |
| ------------- | ---------------------------------------------------------------------------- |
| 201           | Garment Order status was successfully changed                                |
| 403           | Not Authorized - You're not a factory or the garment isn't from your factory |
| 409           | Unable to move to a different status. Reason provided in JSON                |
