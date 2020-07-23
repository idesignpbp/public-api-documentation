# Shipping API

The Shipping API allows a factory to receive raw materials (fabrics) and add a garment to a shipment.

This includes:

- [Create Shipment](#create-shipment) - Add garments to a new shipment
- [Get Shipment Detail](#get-shipment-detail) - Shipment details and garments in the shipment
- [Receive Shipment](#receive-shipment) - Receive a shipment.
- [Get All Fabric Orders](#get-all-fabric-orders) - Get all fabric orders for a specific garment.
- [Get Fabric Order](#get-fabric-order) - Details of a fabric order.
- [Receive Fabric Order](#receive-fabric-order) - Receive a fabric order.
- [Accept Fabric Order](#accept-fabric-order) - Accept a fabric order if it doesn't have any flaws.
- [Reject Fabric Order](#reject-fabric-order) - Reject a flawed fabric order.
- [Fabric Order Errors](#fabric-order-errors) - Report errors with fabric received from fabric order.


## Create Shipment

```shell
curl -X POST "https://api.trinity-apparel.com/v1/shipments"
  -H "Authorization Bearer: swaledale"
```

> The above command returns a `201 Created` and returns a JSON structured like this:

```json
{
    "id": 371421,
    "description": "US Shirts - December 13 #8 from iD Shirts",
    "status": "transit",
    "method": "Worldwide Express",
    "carrier": "FedEx",
    "tracking_number": null,
    "create_date": "2019-12-13T07:05:37.000Z",
    "ship_date": null,
    "receive_date": null,
    "login_id": 1578,
    "source": {
        "id": 1943,
        "description": "Beijing iDesign Garments",
        "street1": "No. 8, Fuqian Street",
        "street2": "Beixiaoying County, Shunyi District",
        "street3": null,
        "city": null,
        "state": "Beijing",
        "zip": "101300",
        "country": "People's Rep. of China",
        "phone": "Tel:  +86 (0)10 60400433"
    },
    "destination": {
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
        },
        ...
    ]
}
```

### Description

This call creates a shipment then adds every garment id that was provided to the shipment. A shipment is just like a packing list.

It also creates a tracking box and tracking box items, which our distribution centers use to track and receive garments from a manufacturer.

### Rules

All items in a shipment must be going to the same destination. If any garment is going to another location the whole shipment fails to be created.

Same rules apply to manufacturers. If any item is from a different manufacturer, the shipment will fail to be created.

### HTTP Request

`POST https://api.trinity-apparel.com/v1/shipments`

### Query Parameters

| Parameter       | Default | Description                                                                         |
| --------------- | ------- | ----------------------------------------------------------------------------------- |
| garment_id[]    | N/A     | An array of garment ids. All garments must be included when the shipment is created |
| tracking_number | null    | Optional. The tracking number for the shipping carrier (E.g., FedEx, DHL, etc)      |

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: N/A

### Responses

| Response Code | Description                                                                  |
| ------------- | ---------------------------------------------------------------------------- |
| 201           | Garment Order status was successfully changed                                |
| 403           | Not Authorized - You're not a factory or the garment isn't from your factory |
| 409           | Unable to move to a different status. Reason provided in JSON                |

## Get Shipment Detail

```shell
curl -X GET "https://api.trinity-apparel.com/v1/shipments/:id"
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
    "supplier": {
        "id": 48,
        "code": "GI",
        "name": "Giovani",
        "city": "",
        "state": null,
        "country": "Hong Kong"
    },
    "source": {
        "id": 1943,
        "description": "Beijing iDesign Garments",
        "street1": "No. 8, Fuqian Street",
        "street2": "Beixiaoying County, Shunyi District",
        "street3": null,
        "city": null,
        "state": "Beijing",
        "zip": "101300",
        "country": "People's Rep. of China",
        "phone": "Tel:  +86 (0)10 60400433"
    },
    "destination": {
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
    ],
    "fabric_orders": [
        {
            "id": 397950,
            "fabric_id": 72898,
            "garment_id": 1143878,
            "length": "1.125",
            "address_id": 12310,
            "extra_fabric": false,
            "fulfillment_failure": false,
            "shipment_id": 385700,
            "reason": "null",
            "created_at": "2020-06-04T00:00:00.000Z",
            "status": "rejected",
            "trinity_fabric_number": "N6-4072898",
            "supplier_fabric_number": "JT 82099-82",
            "description": "White Solid Linen",
            "image": "https://s7d4.scene7.com/is/image/trinityapparel/N6-4072898"
        }
    ]
}
```

### Description

Returns detail on a shipment, which includes the tracking number and destination. It also includes a full list of shipment items.

### Types of Shipments

#### Fabric Order

Fabric Order shipments occur when fabrics shipped from a supplier to a factory. Fabric Orders and Supplier are only returned for fabric order shipments. There will not be any shipment items in a fabric order, since shipment items are a listing of garments in the shipment and this is only for raw materials.

#### Garment Order

Garment order shipments are sent from a factory to a distribution center.  The shipments from our factory to HQ are bulk and are typically part of 10-20 cartons sent each day. Each box is tracked as an individual shipment.  However, direct shipments and shipments to the UK or CA distribution centers are smaller in volume and typically are a single box.

#### Dealer Order

Dealer order shipments are from a distribution center to the final destination, the dealer's shipping address.  They are typically small and are almost always from the HQ distribution center in Ridgeland, MS to another address in the USA.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/shipments/:id`

### Query Parameters

| Parameter | Default | Description                |
| --------- | ------- | -------------------------- |
| id        | N/A     | Lookup id for the shipment |

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: N/A

## Receive Shipment

```shell
curl -X POST "https://api.trinity-apparel.com/v1/shipments/:id/receive"
  -H "Authorization Bearer: swaledale"
```

> The above command returns a JSON structured like this:

```json
{
  "id": 385700,
  "description": "Testing Shipping Fabric Orders",
  "status": "received",
  "method": "Ground",
  "carrier": null,
  "tracking_number": null,
  "create_date": "2020-06-04T00:00:00.000Z",
  "ship_date": "2020-06-04T00:00:00.000Z",
  "receive_date": "2020-06-09T22:14:58.000Z"
}
```

### Description

Sets the status of a shipment to recieved. The shipment must be in `transit` status.

*Note*: Only fabric order shipments can be received at this time.

### HTTP Request

`POST https://api.trinity-apparel.com/v1/shipments/:id/receive`

### Query Parameters

| Parameter | Default | Description                |
| --------- | ------- | -------------------------- |
| id        | N/A     | Lookup id for the shipment |

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: N/A


## Get All Fabric Orders

```shell
curl "https://api.trinity-apparel.com/v1/garments/:id/fabric_orders"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 320723,
        "fabric_id": 29888,
        "garment_id": 1100503,
        "length": "3.75",
        "address_id": 1943,
        "extra_fabric": false,
        "fulfillment_failure": false,
        "shipment_id": null,
        "reason": null,
        "created_at": "2019-12-17T17:35:11.000Z",
        "status": "received",
        "trinity_fabric_number": "L6-3129888",
        "supplier_fabric_number": "360072",
        "description": "Antique Golfers",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/L6-3129888",
        "fabric": {
            "id": 29888,
            "active": true,
            "in_stock": 1,
            "restock_date": null,
            "description": "Antique Golfers",
            "supplier_fabric_number": "360072",
            "trinity_fabric_number": "L6-3129888",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/L6-3129888",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=L6-3129888&res=300",
            "inventory_status": "In Stock",
            "pattern_id": null,
            "weave_id": null,
            "price_tier": 4,
            "discount": null,
            "has_image": true,
            "availability": "unknown",
            "favorite_id": null,
            "fabric_type": null,
            "fabric_garment_type": 0,
            "trim_garment_type": 759
        },
        "address": {
            "id": 1943,
            "description": "Beijing iDesign Garments",
            "street1": "No. 8, Fuqian Street",
            "street2": "Beixiaoying County, Shunyi District",
            "street3": null,
            "city": null,
            "state": "Beijing",
            "zip": "101300",
            "country": "People's Rep. of China",
            "phone": "Tel:  +86 (0)10 60400433"
        },
        "garment": {
            "id": 1100503,
            "title": "ID-1100503",
            "order_id": 505484,
            "copied_garment_id": null,
            "price": "832.0",
            "option_cost": "100.0",
            "garment_type": "CCP",
            "created_at": "2019-12-17T17:35:11.000Z",
            "updated_at": null,
            "order_status_id": 9,
            "delay_status_id": 1,
            "fabric_url": null
        },
        "shipment": null
    },
    {
        "id": 320724,
        "fabric_id": 58067,
        "garment_id": 1100503,
        "length": "4.5",
        "address_id": 1943,
        "extra_fabric": false,
        "fulfillment_failure": false,
        "shipment_id": null,
        "reason": null,
        "created_at": "2019-12-17T17:35:11.000Z",
        "status": "accepted",
        "trinity_fabric_number": "Y4-3858067",
        "supplier_fabric_number": "290015",
        "description": "Slate Puppytooth",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/Y4-3858067",
        "fabric": {
            ...
        },
        "address": {
            ...
        },
        "garment": {
            ...
        },
        "shipment": null
    }
]
```

### Description

Returns an array of fabric orders for a specific garment. Each fabric order includes details on the fabric, address, garment, and shipment attached to it.

*Note*: Almost all fabric orders are generated at checkout. We rarely add them manually to the system.  Sometimes a fabric order will be cancelled (typically when the fabric is out of stock) and a new one will be made when the order is edited and a new fabric is chosen.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/garments/:id/fabric_orders`

### Query Parameters

| Parameter | Default | Description                                            |
| --------- | ------- | ------------------------------------------------------ |
| id        | N/A     | The specific garment you want to get fabric orders for |

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: No

## Get Fabric Order

```shell
curl "https://api.trinity-apparel.com/v1/fabric_orders/:id"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
  "id": 397950,
  "fabric_id": 72898,
  "garment_id": 1143878,
  "length": "1.125",
  "address_id": 12310,
  "extra_fabric": false,
  "fulfillment_failure": false,
  "shipment_id": 385700,
  "reason": "null",
  "created_at": "2020-06-04T00:00:00.000Z",
  "status": "transit",
  "trinity_fabric_number": "N6-4072898",
  "supplier_fabric_number": "JT 82099-82",
  "description": "White Solid Linen",
  "image": "https://s7d4.scene7.com/is/image/trinityapparel/N6-4072898",
  "fabric_composition": "100% Bamboo",
  "fabric": {
    "id": 72898,
    "active": true,
    "in_stock": 1,
    "restock_date": null,
    "description": "White Solid Linen",
    "supplier_fabric_number": "JT 82099-82",
    "trinity_fabric_number": "N6-4072898",
    "url": "https://s7d4.scene7.com/is/image/trinityapparel/N6-4072898",
    "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N6-4072898&res=300",
    "inventory_status": "In Stock",
    "pattern_id": 1,
    "weave_id": null,
    "price_tier": 2,
    "discount": null,
    "has_image": true,
    "availability": "unknown",
    "favorite_id": null,
    "fabric_type": null,
    "fabric_garment_type": 8,
    "trim_garment_type": 0
  },
  "address": {
    "id": 12310,
    "description": "Tyler Jones",
    "street1": "1102 Knox Cove",
    "street2": null,
    "street3": null,
    "city": "Madison",
    "state": "NJ",
    "zip": "59876",
    "country": "USA",
    "phone": "(555)111-2345"
  },
  "garment": {
    "id": 1143878,
    "title": "IDUK-1143878",
    "order_id": 526328,
    "copied_garment_id": 1046085,
    "price": "53.0",
    "option_cost": "0.0",
    "garment_type": "CSHT",
    "created_at": "2020-06-03T00:40:43.000Z",
    "updated_at": "2020-06-03T00:40:43.000Z",
    "order_status_id": 3,
    "delay_status_id": 4,
    "fabric_url": "https://s7d4.scene7.com/is/image/trinityapparel/N6-4072898"
  },
  "shipment": {
    "id": 385700,
    "description": "Testing Shipping Fabric Orders",
    "status": "received",
    "method": "Ground",
    "carrier": null,
    "tracking_number": null,
    "create_date": "2020-06-04T00:00:00.000Z",
    "ship_date": "2020-06-04T00:00:00.000Z",
    "receive_date": "2020-06-09T22:14:58.000Z"
  }
}
```

### Description

Returns details of a fabric order, including details on the fabric, address, garment, and shipment attached to it.

*Note*: Almost all fabric orders are generated at checkout. We rarely add them manually to the system.  Sometimes a fabric order will be cancelled (typically when the fabric is out of stock) and a new one will be made when the order is edited and a new fabric is chosen.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/fabric_orders/:id`

### Query Parameters

| Parameter | Default | Description                               |
| --------- | ------- | ----------------------------------------- |
| id        | N/A     | The specific fabric order you want to see |

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: No

## Receive Fabric Order

```shell
curl -X POST "https://api.trinity-apparel.com/v1/fabric_orders/:id/receive"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
  "id": 397950,
  "fabric_id": 72898,
  "garment_id": 1143878,
  "length": "1.125",
  "address_id": 12310,
  "extra_fabric": false,
  "fulfillment_failure": false,
  "shipment_id": 385700,
  "reason": "null",
  "created_at": "2020-06-04T00:00:00.000Z",
  "status": "received",
  "trinity_fabric_number": "N6-4072898",
  "supplier_fabric_number": "JT 82099-82",
  "description": "White Solid Linen",
  "image": "https://s7d4.scene7.com/is/image/trinityapparel/N6-4072898"
}
```

### Description

This updates the status of a fabric order to be received and returns the fabric order. The fabric must be in the `transit` status before it can be received.

### HTTP Request

`POST https://api.trinity-apparel.com/v1/fabric_orders/:id/receive`

### Query Parameters

| Parameter | Default | Description                                   |
| --------- | ------- | --------------------------------------------- |
| id        | N/A     | The specific fabric order you want to receive |

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: No

## Accept Fabric Order

```shell
curl -X POST "https://api.trinity-apparel.com/v1/fabric_orders/:id/accept"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
  "id": 397950,
  "fabric_id": 72898,
  "garment_id": 1143878,
  "length": "1.125",
  "address_id": 12310,
  "extra_fabric": false,
  "fulfillment_failure": false,
  "shipment_id": 385700,
  "reason": "null",
  "created_at": "2020-06-04T00:00:00.000Z",
  "status": "accepted",
  "trinity_fabric_number": "N6-4072898",
  "supplier_fabric_number": "JT 82099-82",
  "description": "White Solid Linen",
  "image": "https://s7d4.scene7.com/is/image/trinityapparel/N6-4072898"
}
```

### Description

Once a fabric has been received and has passed your inspection process, use this API call to mark it as `accepted` and to confirm the length and width of the fabric you received. We use this information to ensure that our suppliers cut fabrics to the correct dimensions.

Fabric order must have a status of either `transit` or `recieve` to be accepted. This will create a Fabric Checkpoint, set the status of the fabric order to accepted, and also move the garment to the `Ready` order status (as long as all required fabrics have been received). If unsuccessful, it will return the error that was encountered. If successful, it will return the updated fabric order.

If the pattern is solid, you will only need to pass the `cuttable_width`, `cuttable_length` and `fabric_type_code` params.  If the pattern is stripe or check, you will also need to include the `fabric_type_width`.  If the pattern is check, you will also need `fabric_type_length`.

### Detail

The allowed fabric type codes are:

| Code             | Description             |
| ---------------- | ----------------------- |
| check            | Check 1 - Symmetric     |
| check_asymmetric | Check 2 - Asymmetric    |
| solid            | Solid, Paisley or Other |
| stripe           | Stripe                  |

### HTTP Request

`POST https://api.trinity-apparel.com/v1/fabric_orders/:id/accept`

### Query Parameters

| Parameter          | Default | Description                                                                                   |
| ------------------ | ------- | --------------------------------------------------------------------------------------------- |
| id                 | N/A     | The specific fabric order you want to accept                                                  |
| cuttable_length    | N/A     | The cuttable length of the fabric                                                             |
| cuttable_width     | N/A     | The cuttable width of the fabric                                                              |
| fabric_type_code   | N/A     | The code for the fabric pattern (see above)                                                   |
| fabric_type_length | N/A     | The length of the fabric pattern (only needed for check and check_asymmetric patterns)        |
| fabric_type_width  | N/A     | The width of the fabric pattern (only needed for stripe, check and check_asymmetric patterns) |

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: No

## Reject Fabric Order

```shell
curl -X POST "https://api.trinity-apparel.com/v1/fabric_orders/:id/reject"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
  "fabric_order": {
    "id": 397950,
    "status": "rejected",
    "garment_id": 1143878,
    "fabric_id": 72898,
    "address_id": 12310,
    "length": "1.125",
    "shipment_id": 385700,
    "login_id": 1710,
    "extra_fabric": false,
    "fulfillment_failure": false,
    "reason": "null",
    "created_at": "2020-06-04T00:00:00.000Z",
    "updated_at": "2020-06-09T21:37:47.000Z"
  },
  "new_fabric_order": {
    "id": 397968,
    "status": "pending",
    "fabric_id": 72898,
    "address_id": 12310,
    "garment_id": 1143878,
    "length": "1.125",
    "extra_fabric": true,
    "fulfillment_failure": false,
    "shipment_id": 385700,
    "login_id": 1578,
    "reason": "flawed",
    "created_at": null,
    "updated_at": null
  }
}
```

### Description

**WARNING** This API call will automatically place a new fabric order with the vendor as long as the fabric is in stock.

Use this API call after you receive a fabric and the fabric fails your inspection process. You'll mark the reason it was rejected and we can usually automatically reorder it from the supplier.

Fabric orders must have a status of either `transit` or `recieved` to be rejected. This will move the garment into the correct delay status (typically no delay) and set the status of the fabric order to `rejected`. It will also create a new fabric order as long as the fabric is in stock and the reason isn't due to a fabric short. If either the fabric was short or out of stock, a fabric order will have to be placed manually.

If everything was successful, you will get back an updated copy of the current fabric order as well as the newly placed fabric order (same fabric but the length you specified). If there was an error, the error message will be returned. And if the new_fabric_order is null, that means a new order was unable to be placed automatically and will have to be done manually.


### Detail

The allowed reason codes are:

| Code    | Description      |
| ------- | ---------------- |
| part    | Alteration Parts |
| short   | Fabric Short     |
| mistake | Factory Mistake  |
| dirty   | Fabric Dirty     |
| flawed  | Fabric Flawed    |
| hole    | Fabric has Holes |
| warped  | Fabric is Warped |
| wrong   | Wrong Fabric     |

### HTTP Request

`POST https://api.trinity-apparel.com/v1/fabric_orders/:id/reject`

### Query Parameters

| Parameter   | Default | Description                                                                                                                                           |
| ----------- | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| id          | N/A     | The specific fabric order you want to reject                                                                                                          |
| reason_code | N/A     | The reason you are rejecting the fabric                                                                                                               |
| length      | N/A     | The total yards needed when reordering (optional, only include when different from the cut you received). Default is length of the order that arrived |

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: No

## Fabric Order Errors

```shell
curl -X POST "https://api.trinity-apparel.com/v1/fabric_orders/:id/errors"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
  "id_fabric_errors": 397953,
  "position_x": 22,
  "position_y": 12,
  "length": 15.0,
  "width": 17.0,
  "id_fabric_checkpoint": 397951
}
```

### Description

This is to set errors found on a fabric. In order to record errors, the fabric order must be received by the factory (status of `received` or `accepted`). This will create and return a Fabric Error record that will define the coordinates for the unusable spot on the fabric.

### HTTP Request

`POST https://api.trinity-apparel.com/v1/fabric_orders/:id/errors`

### Query Parameters

| Parameter  | Default | Description                                         |
| ---------- | ------- | --------------------------------------------------- |
| id         | N/A     | The specific fabric order you want to set errors on |
| position_x | N/A     | The X position of the error on the fabric           |
| position_y | N/A     | The Y position of the error on the fabric           |
| length     | N/A     | The total length of the error spot on the fabric    |
| width      | N/A     | The total width of the error spot on the fabric     |

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: No
