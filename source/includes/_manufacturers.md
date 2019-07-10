# Manufacturers API

The manufacturers API allows a factory to download all relevant information needed to produce a garment. Plus it allows the factory to update the status of a garment and add the garment to a shipment.

This includes:

- [Download Garments](#download-garments) - a list of new garment orders that are ready to be produced by the factory
- [Garment Detail](#get-a-specific-garment)
- [Garment Properties](#garment-properties) - Get Options and Measurements for a specific garment
- [Garment Fabrics](#get-garment-fabrics) - Get a list of fabrics needed, what they are used for (shell, lining, trims, etc), and see their measurments and status
- [Set Order Status](#set-order-status) - E.g., Move a garment from Ready to Production
- [Create Shipment](#create-shipment) - Add garments to a new shipment
- [Get Shipment Detail](#get-shipment-detail) - Shipment details and garments in the shipment


## Order Processing Flow

`Ready` -> `Blue Pencil` -> `Cutting` -> `Production` -> `Production Complete` -> `International Transit`

### Ready status

Garment can be downloaded if it is not in a delay status (trinity review of special instructions, etc). Downloading involves getting garment detail, garment properties, garment fabrics, and downloading the gerber files.

Once the garment is fully downloaded, the manufacturer should move the garment to Blue Pencil status (ID=4 or code=PENDING).

### Blue Pencil status

In Blue Pencil status, the CAD team lays the marker, the order team puts the order in the production plan, and materials are gathered.  Once the marker is complete, the factory should input the CAD measurements into Trinity Admin on the `Fabric Cuts` page: https://admin.trinity-apparel.com/fabric_cuts

When all fabric cut lengths are entered into the system, the garment will be automatically moved into cutting.

### Cutting status

Once all fabrics (shell, lining, trims, etc) have been cut, the garment should be moved to Production status (ID=5 or code=PRODUCTION) using the set order status call.

### Production status

During the production process we print care labels and hang tags.  You will use our Windows applications to print these.  These applications require internet connectivity to hit our api and get data about the garment.

For garments with embroidery, you need to use two Windows applications.  One must be connected to a computer with the App Ethos software installed and have the App Ethos dongle.  It cannot be a server and will not allow remote desktop connections while the app is running.  Our app connects to our API and gets data about embroidery and generates an input file that app ethos uses to create a DST file.  The file can either sit on a share drive or be moved manually using a USB key.  The second embroidery app reads the DST files and provides them to a Brother embroidery machine.

Once production is complete and the garment is ready to ship. Please set the order status to production complete (ID=6 or code=MADE).

### Production complete status

In the production complete status, we build a packing list using the create shipment call.  We can add a tracking number immediately or add one at a later time.  Once the shipment has a tracking number, we can move the garments to international transit (set status to ID=7 or code=SHIPDC).

### International Transit status

Trinity will take the order from here.  Once we receive the garment at a distribution center, we will move the status to final inspection.


## Resources

The resources provided by the manufacturers API are almost identical to the orders API.  Only the garment and dealer_order objects are different. Links to download Gerber input files and the order PDFs are included.

### Garment

```json
# Standard Object - Used in a resource collection
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

| Attribute                                   | Description                                                                                                      |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| id <br> <span>integer</span>                | Unique identifier for the object                                                                                 |
| title <br> <span>string</span>              | Our SKU field which includes the garment id number and information about where the factory will send the garment |
| order_id <br> <span>integer</span>          | Each garment must be a part of a specific order                                                                  |
| copied_garment_id <br> <span>integer</span> | Garment id if this was copied from a previous order                                                              |
| garment_type <br> <span>string</span>       | Type of garment. [Click here](#garment-types) for more info                                                      |
| prefix <br> <span>string</span>             | First part of the title. This indicates where the order was made or where the factory will send the garment      |
| index <br> <span>string</span>              | Sequence number (1/7, 2/7, 3/7 ...) for each garment in an order. Each item has a different index                |
| created_at <br> <span>datetime</span>       | When the garment was first created (but not ordered)                                                             |
| updated_at <br> <span>datetime</span>       | When the garment was last modified                                                                               |
| last_status_change_date <br> <span>datetime</span>     | When did the order status last change to a new state                                                  |
| last_delay_change_date  <br> <span>datetime</span>     | When did the delay status last change to a new state                                                  |
| links <br> <span>subresource</span>         | Urls that allow the manufacturer to generate Gerber ASCII files, an Order Insert PDF, and an Order Split         | 
| manufacturer <br> <span>subresource</span>  | Factory that made the order. [Click here](#manfacturers) for more info                                           |
| fabric <br> <span>subresource</span>        | Shell fabric used in the order. [Click here](#fabrics) for more info                                             |
| order_status <br> <span>subresource</span>  | Current status of the order. [Click here](#order-statuses) for more info                                         |
| delay_status <br> <span>subresource</span>  | If garment is delayed, this will return why. [Click here](#delay-statuses) for more info                         |
| dealer_order <br> <span>subresource</span>  | The full order placed by a single customer. Includes this garment and can include more garments.                 |


### Dealer Order

```json
# Standard Object - Used in a resource collection
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

| Attribute                                    | Description                                                                                                                                                                                                           |
| -------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id <br> <span>string</span>                  | Unique identifier for the object                                                                                                                                                                                      |
| title <br> <span>string</span>               | Our SKU field for orders                                                                                                                                                                                              |
| custom_order_number <br> <span>string</span> | Dealers can set this field to whatever they want.  It is typically the dealer's SKU or a summary of the order                                                                                                         |
| garment_count <br> <span>integer</span>      | How many garments are in the order. multi-piece garments (e.g., Suit) are counted as 1.                                                                                                                               |
| ship_type <br> <span>string</span>           | How is the garment shipped to the final destination                                                                                                                                                                   |
| measurement_units <br> <span>string</span>   | Units can be `uscust` for US customary units (in) or `si` for metric units (cm)                                                                                                                                       |                                                                                          |
| ordered_at <br> <span>datetime</span>        | Time that the dealer completed the checkout process and officially placed the order                                                                                                                                   |
| created_at <br> <span>datetime</span>        | Time when the dealer first began adding garments to the order                                                                                                                                                         |
| invoiced_at <br> <span>datetime</span>       | Time of the first invoice                                                                                                                                                                                             |


## Download Garments

```shell
curl "https://api.trinity-apparel.com/v1/download_garments"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 845546,
        "title": "TEST-845546",
        "order_id": 386627,
        "copied_garment_id": null,
        "garment_type": "CTOPC",
        "prefix": "TEST",
        "index": "",
        "created_at": "2018-04-24T20:36:53.000Z",
        "updated_at": null,
        "last_status_change_date": "2018-04-24T20:36:53.000Z",
        "last_delay_change_date": null,
        "links": {
            "gerber": "http://localhost:8080/share/order_insert.php?suit_ids[]=845546&units=uscust&format=gerber&fabtype=both",
            "order_insert": "https://trinity-apparel.com/share/order_insert.php?format=pdfzip&units=si&suit_ids%5B%5D=845546",
            "order_split": "https://documents.trinity-apparel.com/order_splits?garment_id=845546&locale=en"
        },
        "manufacturer": {
            "id": 5,
            "name": "Trisco TAM",
            "email": "info@trinity-apparel.com"
        },
        "fabric": {
            "id": 41803,
            "active": true,
            "in_stock": 1,
            "restock_date": null,
            "description": "Dark Navy White Plaid",
            "supplier_fabric_number": "641 139 900",
            "trinity_fabric_number": "Z4-3541803",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z4-3541803",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z4-3541803&res=300",
            "inventory_status": "In Stock",
            "pattern_id": 4,
            "weave_id": null,
            "price_tier": 3,
            "discount": null,
            "has_image": false,
            "availability": "single-cut",
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
        }
    },
    ...
]
```

Returns an array of garments that are ready for download.

Right after a customer places an order, Trinity validates the order and requests materials if needed.  Once the order is validated and fabric is received, it moves out of a hold status and is ready for download.  These garments are in `Ready` status and have no delay status.

We expect the manufacturer to get a list of garments, then get garment details, fabric, options and measurements info.  Once this is obtained, they will move the order status to `Blue Pencil`, which means that the factory downloaded the order and is laying the marker and putting the order into the production plan. When those tasks are completed the order moves to `Cutting` and then to `Production`.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/download_garments`

### Query Parameters

| Parameter       | Default | Description                                                       |
| --------------- | ------- | ----------------------------------------------------------------- |
| garment_id      | N/A     | Filter the list to a specific garment_id or list of garment_ids (using `garment_id[]=` array style syntax) |
| manufacturer_id | N/A     | If set, returns only garments from a specific manufacturer id     |

### Other

- Permissions: Only manufacturers can access this route.  They can only see garments made at their factory.
- Pagination: Yes

### Examples 

#### Download from a specific manufacturer

`GET https://api.trinity-apparel.com/v1/download_garments?manufacturer_id=4`

Returns garments from a specific factory

#### Download specific garments

`GET https://api.trinity-apparel.com/v1/download_garments?garment_id[]=1001234&garment_id[]=1002345&garment_id[]=1003456`

Returns garments #1001234, #1002345, and #1003456 as long as they are in `Ready` status and have no delays.


## Garment Properties

**NOTE**: This is a temporary url that will change in the next few weeks

```shell
curl "https://dev.trinity-apparel.com/properties/v1/garment_properties/:id"
```

> The above command returns JSON structured like this:

```json
{
  "measurements": [
    {
      "id": 2,
      "name": "height",
      "description": "Height",
      "value": 182.9,
      "last_modified": "2019-07-06 04:43:30 UTC"
    },
    {
      "id": 3,
      "name": "weight",
      "description": "Weight",
      "value": 533.4,
      "last_modified": "2019-07-06 04:43:30 UTC"
    },
    {
      "id": 6,
      "name": "coat_fit",
      "description": "Coat Fit",
      "value": "trim",
      "last_modified": "2019-07-06 04:43:30 UTC"
    },
    {
      "id": 7,
      "name": "perkins_incline",
      "description": "Incline Reading",
      "value": 8.3,
      "last_modified": "2019-07-06 04:43:30 UTC"
    },
    ...
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
        "description": "Dealer Private Label"
      }
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
        "description": "Side Vents"
      }
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
        "description": "Ultra Soft"
      }
    },
    {
      "option": {
        "id": 4,
        "name": "exterior_breast_pocket",
        "description": "Exterior Breast Pocket"
      },
      "option_value": {
        "id": 10,
        "value": "welt",
        "description": "Welt (Standard)"
      }
    },
    ...

}
```

Returns an array of `measurements` and an array of `options`.

All measurements are converted into the appropriate measurement units for the factory (typically CM) and measurements are adjusted to be finished.  Synthetic measurements are calculated and inserted into this list.

All options are shown with the option id, name and description, plus the option value name, localized description, and text (if entered by the dealer).


### HTTP Request

`GET https://dev.trinity-apparel.com/properties/v1/garment_properties/:id`

### Query Parameters

| Parameter       | Default | Description                                                       |
| --------------- | ------- | ----------------------------------------------------------------- |
| id              | N/A     | The specific garment you want fabrics for                         |

### Other

- Permissions: Only manufacturers can access this route.  They can only see garments made at their factory.
- Pagination: No


## Get Garment Fabrics

```shell
curl "https://api.trinity-apparel.com/v1/garments/:id/fabrics"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "fabric": {
            "id": 39988,
            "active": true,
            "in_stock": 1,
            "restock_date": null,
            "description": "Blue Sharkskin",
            "supplier_fabric_number": "223.046/44",
            "trinity_fabric_number": "Z2-3339988",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/Z2-3339988",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=Z2-3339988&res=300",
            "inventory_status": "In Stock",
            "pattern_id": null,
            "weave_id": 15,
            "price_tier": 3,
            "discount": null,
            "has_image": true,
            "availability": "at once",
            "favorite_id": null,
            "fabric_type": null,
            "fabric_garment_type": 199,
            "trim_garment_type": 0
        },
        "options": [
            {
                "option_id": null,
                "name": "shell",
                "description": "Shell Fabric",
                "garment_types": [
                    {
                        "name": "Coat",
                        "abbreviation": "CSC",
                        "garment_type": 1
                    },
                    {
                        "name": "Pant",
                        "abbreviation": "CT",
                        "garment_type": 4
                    }
                ]
            }
        ],
        "errors": [],
        "measurements": {
            "estimated": {
                "width": null,
                "length": null,
                "type": null
            },
            "cad": {
                "width": 146,
                "length": 320,
                "is_cut": false
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
    {
        "fabric": {
            "id": 40676,
            "active": true,
            "in_stock": 1,
            "restock_date": null,
            "description": "Royal Blue Fancy",
            "supplier_fabric_number": "L4-3540676",
            "trinity_fabric_number": "L4-3540676",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/L4-3540676",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=L4-3540676&res=300",
            "inventory_status": "In Stock",
            "pattern_id": 35,
            "weave_id": null,
            "price_tier": 3,
            "discount": null,
            "has_image": true,
            "availability": "at once",
            "favorite_id": null,
            "fabric_type": null,
            "fabric_garment_type": 0,
            "trim_garment_type": 759
        },
        "options": [
            {
                "option_id": 510,
                "name": "materials_lining_fabric_num",
                "description": "Lining Fabric #",
                "garment_types": [
                    {
                        "name": "Coat",
                        "abbreviation": "CSC",
                        "garment_type": 1
                    }
                ]
            },
            {
                "option_id": 229,
                "name": "lining_fabric_num",
                "description": "Lining Fabric #",
                "garment_types": [
                    {
                        "name": "Coat",
                        "abbreviation": "CSC",
                        "garment_type": 1
                    }
                ]
            }
        ],
        "errors": [],
        "measurements": {
            "estimated": {
                "width": null,
                "length": null,
                "type": null
            },
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
]
```

Returns an array of fabrics that are used to make a garment.  Under each fabric we list the options it is used for, as well as the shell fabric.  This uses a simple garment option subresource that identifies the option id, name, description, and garment types for the option.  Errors are indicated if a fabric was damaged or short. We also include information about fabric measurements.

| Measurement      | Fabric Source | Description                                                      |
| ---------------- | ------------- | --------------------------------------------------------------- |
| estimated        | Single-Length | Estimated fabric length needed. Provided to fabric suppliers at checkout     |
| received         | Single-Length | Measured length and width of single-length fabric provided by a supplier |
| repeated_pattern | Single-Length | Optional; Pattern width of stripes or length and width of check |
| cad              | All           | Length and width needed by CAD marker                           |

### HTTP Request

`GET https://api.trinity-apparel.com/v1/garments/:id/fabrics`

### Query Parameters

| Parameter       | Default | Description                                                       |
| --------------- | ------- | ----------------------------------------------------------------- |
| id              | N/A     | The specific garment you want fabrics for                         |

### Other

- Permissions: Only manufacturers can access this route.  They can only see garments made at their factory.
- Pagination: No


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

Trinity enforces strict validation rules so that garments can only move to a few order statuses from any given status.  Here are the valid transitions for each status:

| Starting Status | Valid Destination Status                                          |
| --------------- | ----------------------------------------------------------------- |
| Incomplete      | CMT Fabric Hold, Fabric Hold, Ready, Cancelled                    |
| CMT Fabric Hold | Fabric Hold, Ready, Cancelled                                     |
| Fabric Hold     | Ready, Cancelled                                                  |
| Ready           | Blue Pencil, Cutting, Production, Cancelled                       |
| Blue Pencil     | Cutting, Production, Production Complete, Cancelled               |
| Cutting         | Production, Production Complete, Cancelled                        |
| Production      | Production Complete, International Transit, Cancelled             |
| Production Complete | International Transit, Direct Ship, Cancelled                 |
| International Transit | Final Inspection, Shipment Processing, Direct Ship, Cancelled |
| Final Inspection | Shipment Processing, Delivery, Direct Ship, Cancelled            |
| Shipment Processing |  Delivery, Direct Ship, Cancelled                             |
| Delivery        | Shipment Processing, Cancelled                                    |
| Direct Ship     | Production Complete, Cancelled                                    |
| Cancelled       |                                                                   |

### HTTP Request

`GET https://api.trinity-apparel.com/v1/garments/:id/order_statuses/:order_status`

### Query Parameters

| Parameter       | Default | Description                                                       |
| --------------- | ------- | ----------------------------------------------------------------- |
| order_status    | N/A     | Can be an id number or a code. [Click here](#order-statuses) for more info |

### Other

- Permissions: Only manufacturers can access this route.  They can only see garments made at their factory.
- Pagination: N/A

### Responses

| Response Code   | Description                                                       |
| --------------- | ----------------------------------------------------------------- |
| 201             | Garment Order status was successfully changed                     |
| 403             | Not Authorized - You're not a factory or the garment isn't from your factory |
| 409             | Unable to move to a different status. Reason provided in JSON     |


## Create Shipment

```shell
curl -X POST "https://api.trinity-apparel.com/v1/shipments"
  -H "Authorization Bearer: swaledale"
```

> The above command returns a `201 Created` and returns a JSON structured like this:

```json
{
    "id": 356907,
    "description": "US Shirts - July 09 #1 from iD Shirts",
    "status": "transit",
    "method": "Worldwide Express",
    "carrier": "FedEx",
    "tracking_number": null,
    "create_date": "2019-07-09T10:18:07.000Z",
    "ship_date": null,
    "receive_date": null,
    "login_id": 1578,
    "address": {
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
    },
    "shipment_items": [
        {
            "id": 1855007,
            "item_id": 941358,
            "created_at": "2019-07-09T10:18:07.000Z"
        }
    ]
}
```

### Description

This call creates a shipment then adds every garment id that was provided to the shipment.  A shipment is just like a packing list.

It also creates a tracking box and tracking box items, which our distribution centers use to track and receive garments from a manufacturer.

### Rules

All items in a shipment must be going to the same destination.  If any garment is going to another location the whole shipment fails to be created.

Same rules apply to manufacturers.  If any item is from a different manufacturer, the shipment will fail to be created.

### HTTP Request

`POST https://api.trinity-apparel.com/v1/shipments`

### Query Parameters

| Parameter       | Default | Description                                                       |
| --------------- | ------- | ----------------------------------------------------------------- |
| garment_id[]    | N/A     | An array of garment ids.  All garments must be included when the shipment is created |
| tracking_number | null    | Optional. The tracking number for the shipping carrier (E.g., FedEx, DHL, etc) |

### Other

- Permissions: Only manufacturers can access this route.  They can only see garments made at their factory.
- Pagination: N/A

### Responses

| Response Code   | Description                                                       |
| --------------- | ----------------------------------------------------------------- |
| 201             | Garment Order status was successfully changed                     |
| 403             | Not Authorized - You're not a factory or the garment isn't from your factory |
| 409             | Unable to move to a different status. Reason provided in JSON     |


## Get Shipment Detail

```shell
curl -X POST "https://api.trinity-apparel.com/v1/shipments/:id"
  -H "Authorization Bearer: swaledale"
```

> The above command returns a JSON structured like this:

```json
{
    "id": 351907,
    "description": "UK Shirts - May 22 #6 from iD Shirts",
    "status": "received",
    "method": "Worldwide Express",
    "carrier": "FedEx",
    "tracking_number": "485590026995",
    "create_date": "2019-05-22T06:58:58.000Z",
    "ship_date": "2019-05-22T02:52:14.000Z",
    "receive_date": "2019-05-29T08:12:59.000Z",
    "login_id": 1026,
    "address": {
        "id": 1222,
        "description": "Trinity UK Shipping",
        "street1": "8 George St.",
        "street2": null,
        "street3": null,
        "city": "Alderley Edge",
        "state": null,
        "zip": "SK9 7EJ",
        "country": "U.K.",
        "phone": null
    },
    "shipment_items": [
        {
            "id": 1819962,
            "item_id": 996625,
            "created_at": "2019-05-22T06:58:58.000Z"
        },
        {
            "id": 1819965,
            "item_id": 996626,
            "created_at": "2019-05-22T06:58:58.000Z"
        },
        {
            "id": 1819963,
            "item_id": 996627,
            "created_at": "2019-05-22T06:58:58.000Z"
        },
        {
            "id": 1819969,
            "item_id": 996630,
            "created_at": "2019-05-22T06:58:58.000Z"
        },
        ...
    }
}
```

### Description

Returns detail on a shipment, which includes the tracking number and destination.  It also includes a full list of shipment items.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/shipments/:id`

### Query Parameters

| Parameter       | Default | Description                                                       |
| --------------- | ------- | ----------------------------------------------------------------- |
| id              | N/A     | Lookup id for the shipment                                        |

### Other

- Permissions: Only manufacturers can access this route.  They can only see garments made at their factory.
- Pagination: N/A


