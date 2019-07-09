# Manufacturers API

The manufacturers API allows a factory to download all relevant information needed to produce a garment. Plus it allows the factory to update the status of a garment and add the garment to a shipment.

This includes:

- Download Garments - a list of new garment orders that are ready to be produced by the factory
- Garment Detail
- Garment Properties - Get Options and Measurements for a specific garment
- Garment Fabrics - Get a list of fabrics needed, what they are used for (shell, lining, trims, etc), and see their measurments and status
- Set Order Status - E.g., Move a garment from Ready to Production
- Create Shipment - Add garments to a new shipment

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


## Download Orders

```shell
curl "https://api.trinity-apparel.com/v1/download_orders"
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

`GET https://api.trinity-apparel.com/v1/download_orders`

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

`GET https://api.trinity-apparel.com/v1/download_orders?manufacturer_id=4`

Returns garments from a specific factory

#### Download specific garments

`GET https://api.trinity-apparel.com/v1/download_orders?garment_id[]=1001234&garment_id[]=1002345&garment_id[]=1003456`

Returns garments #1001234, #1002345, and #1003456 as long as they are in `Ready` status and have no delays.

