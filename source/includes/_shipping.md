# Shipping API

The Shipping API allows a factory to receive raw materials (fabrics) and add a garment to a shipment.

This includes:

- [Create Shipment](#create-shipment) - Add garments to a new shipment
- [Get Shipment Detail](#get-shipment-detail) - Shipment details and garments in the shipment
- [Receive Shipment](#receive-shipment) - Receive a shipment.
- [Get All Fabric Shipments](#get-fabric-shipments) - Shipment details for ONLY shipments containing fabric orders.
- [Get All Fabric Orders](#get-all-fabric-orders) - Get all fabric orders for a specific garment.
- [Get Fabric Order](#get-fabric-order) - Details of a fabric order.
- [Receive Fabric Order](#receive-fabric-order) - Receive a fabric order.
- [Accept Fabric Order](#accept-fabric-order) - Accept a fabric order if it doesn't have any flaws.
- [Reject Fabric Order](#reject-fabric-order) - Reject a flawed fabric order.
- [Fabric Order Errors](#fabric-order-errors) - Report errors with fabric received from fabric order.
- [Accept CMT Fabric](#accept-cmt-fabric) - Accept a CMT fabric if it doesn't have any flaws.
- [Reject CMT Fabric](#reject-cmt-fabric) - Reject a flawed CMT fabric.

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

All items in a shipment must be going to the same destination. If any garment is going to another location the whole shipment fails to be created. Although the first check should cover this case, all garments in a shipment should be of the same shipping class.

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

## Complete Shipment

```shell
curl -X POST "https://api.trinity-apparel.com/v1/shipments/:id/complete"
  -H "Authorization Bearer: swaledale"
```

> The above command returns a `201 Created` and returns a JSON structured like this:

```json
{
    "id": 507121,
    "description": "US Suits - November 17 #2 from T2iD MTM",
    "status": "transit",
    "method": "Worldwide Express",
    "carrier": "UPS",
    "tracking_number": "1Z9F23146639469257",
    "receive_date": null,
    "create_date": "2023-11-17T21:36:56.000Z",
    "ship_date": "2023-11-17T21:37:38.000Z",
    "shipment_type": "garment order",
    "login_id": 1862,
    "supplier": null,
    "source": {
        "id": 2343,
        "contact_name": "Verawati Roma Uli",
        "description": "PT. Trisco",
        "street1": "Jl. Raya Kopo - Soreang",
        "street2": "KM. 11.5 Katapang - Soreang",
        "street3": null,
        "city": "Bandung",
        "state": "Jawa Barat",
        "zip": "40971",
        "country": "Indonesia",
        "phone": "+62-22 589 7185"
    },
    "destination": {
        "id": 1,
        "contact_name": "Trinity Apparel Group, LLC",
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
            "id": 2747629,
            "item_id": 1520852,
            "created_at": "2023-11-17T21:36:56.000Z"
        },
        {
            "id": 2747630,
            "item_id": 1520868,
            "created_at": "2023-11-17T21:36:56.000Z"
        }
    ],
    "fabric_orders": []
}
```

### Description

This call finalizes a shipment and moves the status of the shipment to 'transit'. If the tracking number for the shipment was not known at the time the shipment was created, it can be updated with the optional tracking number parameter. This call will also move all garments contained in the shipment to the status of 'International Transit'. 

### Rules

A shipment ID must be provided and the status of that shipment must be Pending. If the shipment is not pending, the shipment will fail to be completed.

As shipment can only be completed by the manufacturer who created the shipment.

Again, we check to ensure all garments contained in the shipment are of the same shipping class, either Direct or Garment Order. If any garment is of a different shipping class, the shipment will fail to be completed.



### HTTP Request

`POST https://api.trinity-apparel.com/v1/shipments/:id/complete`

### Query Parameters

| Parameter       | Default | Description                                                                         |
| --------------- | ------- | ----------------------------------------------------------------------------------- |
| shipment_id    | N/A     | The id of the shipment you are wishing to complete |
| tracking_number | null    | Optional. The tracking number for the shipping carrier (E.g., FedEx, DHL, etc)      |

### Other

- Permissions: Only manufacturers can access this route. They can only complete shipments originating from their location.
- Bulk and Garment Order are used interchangeably as a shipment class.
- Pagination: N/A

### Responses

| Response Code | Description                                                                  |
| ------------- | ---------------------------------------------------------------------------- |
| 201           | Shipment successfully completed                                |
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
    "shipment_type": "bulk",
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
            "image": "https://s7d4.scene7.com/is/image/trinityapparel/N6-4072898",
            "material_type": "Fabric"
        }
    ]
}
```

### Description

Returns detail on a shipment, which includes the tracking number and destination. It also includes a full list of shipment items.

### Types of Shipments

#### Fabric Order

Fabric Order shipments occur when fabrics shipped from a supplier to a factory. Fabric Orders and Supplier are only returned for fabric order shipments. There will not be any shipment items in a fabric order, since shipment items are a listing of garments in the shipment and this is only for raw materials.

#### Shipment Type
Shipments are either direct ship or bulk. Direct ship means the shipment is going directly to a customer. Bulk means the shipment is going to a distribution center.

#### Garment Order

Garment order shipments are sent from a factory to a distribution center. The shipments from our factory to HQ are bulk and are typically part of 10-20 cartons sent each day. Each box is tracked as an individual shipment. However, direct shipments and shipments to the UK or CA distribution centers are smaller in volume and typically are a single box.

#### Dealer Order

Dealer order shipments are from a distribution center to the final destination, the dealer's shipping address. They are typically small and are almost always from the HQ distribution center in Ridgeland, MS to another address in the USA.

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

_Note_: Only fabric order shipments can be received at this time.

### HTTP Request

`POST https://api.trinity-apparel.com/v1/shipments/:id/receive`

### Query Parameters

| Parameter | Default | Description                |
| --------- | ------- | -------------------------- |
| id        | N/A     | Lookup id for the shipment |

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: N/A

## Get Fabric Shipments

```shell
curl -X GET "https://api.trinity-apparel.com/v1/fabric_shipments"
  -H "Authorization Bearer: swaledale"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "id": 388757,
    "description": "Fabric Orders 07/16/20 from Giovani to Trinity USA",
    "status": "received",
    "method": null,
    "carrier": "DHL",
    "tracking_number": "8341286236",
    "create_date": "2020-07-16T04:31:51.000Z",
    "ship_date": "2020-07-16T04:33:15.000Z",
    "receive_date": "2020-07-23T06:26:27.000Z",
    "login_id": 2,
    "packing_list_url": "https://workflow.trinity-apparel.com/supplier/shipment_packing_list.php?shipment_id=388757&token=eyJhbGciOiJSUzI1NiJ9",
    "invoice_url": "https://workflow.trinity-apparel.com/supplier/shipment_invoice.php?shipment_id=388757&token=eyJhbGciOiJSUzI1NiJ9",
    "supplier": {
      "id": 48,
      "code": "GI",
      "name": "Giovani",
      "city": "Samphanthawong",
      "state": "Bangkok",
      "country": "Thailand"
    },
    "source": {
      "id": 14431,
      "description": "Warehouse Address",
      "street1": "161 Vanich 1 Road (Sampheng)",
      "street2": "Chakrawat",
      "street3": null,
      "city": "Samphanthawong",
      "state": "Bangkok",
      "zip": "10100",
      "country": "Thailand",
      "phone": "(66) 02 2229190"
    },
    "destination": {
      "id": 2343,
      "description": "PT. Trisco",
      "street1": "Jl. Raya Kopo - Soreang",
      "street2": "KM. 11.5 Katapang - Soreang",
      "street3": null,
      "city": "Bandung",
      "state": "Jawa Barat",
      "zip": "40971",
      "country": "Indonesia",
      "phone": "+62-22 589 7185"
    },
    "shipment_items": [],
    "fabric_orders": [
      {
        "id": 400569,
        "fabric_id": 84544,
        "garment_id": 1152408,
        "length": "2.375",
        "address_id": 2343,
        "extra_fabric": false,
        "fulfillment_failure": false,
        "shipment_id": 388757,
        "reason": null,
        "created_at": "2020-07-15T19:41:29.000Z",
        "status": "accepted",
        "trinity_fabric_number": "TT-4184544",
        "supplier_fabric_number": "T547",
        "description": "Blue Shepard Twill Check",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/TT-4184544",
        "material_type": "Fabric"
      },
      {
        "id": 400570,
        "fabric_id": 84544,
        "garment_id": 1152409,
        "length": "2.375",
        "address_id": 2343,
        "extra_fabric": false,
        "fulfillment_failure": false,
        "shipment_id": 388757,
        "reason": null,
        "created_at": "2020-07-15T19:41:29.000Z",
        "status": "accepted",
        "trinity_fabric_number": "TT-4184544",
        "supplier_fabric_number": "T547",
        "description": "Blue Shepard Twill Check",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/TT-4184544",
        "material_type": "Fabric"
      },
      {
        "id": 400571,
        "fabric_id": 84544,
        "garment_id": 1152410,
        "length": "2.375",
        "address_id": 2343,
        "extra_fabric": false,
        "fulfillment_failure": false,
        "shipment_id": 388757,
        "reason": null,
        "created_at": "2020-07-15T19:41:29.000Z",
        "status": "accepted",
        "trinity_fabric_number": "TT-4184544",
        "supplier_fabric_number": "T547",
        "description": "Blue Shepard Twill Check",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/TT-4184544",
        "material_type": "Fabric"
      },
      {
        "id": 400572,
        "fabric_id": 84544,
        "garment_id": 1152411,
        "length": "2.375",
        "address_id": 2343,
        "extra_fabric": false,
        "fulfillment_failure": false,
        "shipment_id": 388757,
        "reason": null,
        "created_at": "2020-07-15T19:41:29.000Z",
        "status": "accepted",
        "trinity_fabric_number": "TT-4184544",
        "supplier_fabric_number": "T547",
        "description": "Blue Shepard Twill Check",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/TT-4184544",
        "material_type": "Fabric"
      }
    ]
  },
  {
    "id": 389426,
    "description": "Fabric Orders 07/29/20 from RDL to PT. Trisco",
    "status": "received",
    "method": null,
    "carrier": "DHL",
    "tracking_number": "1943555036",
    "create_date": "2020-07-29T03:05:04.000Z",
    "ship_date": "2020-07-29T03:12:06.000Z",
    "receive_date": "2020-08-04T06:21:21.000Z",
    "login_id": 2,
    "packing_list_url": "https://workflow.trinity-apparel.com/supplier/shipment_packing_list.php?shipment_id=389426&token=eyJhbGciOiJSUzI1NiJ9",
    "invoice_url": "https://workflow.trinity-apparel.com/supplier/shipment_invoice.php?shipment_id=389426&token=eyJhbGciOiJSUzI1NiJ9",
    "supplier": {
      "id": 19,
      "code": "RD",
      "name": "RDL",
      "city": "Tsim Sha Tsui",
      "state": "Kowloon",
      "country": "Hong Kong"
    },
    "source": {
      "id": 14413,
      "description": "Warehouse Address",
      "street1": "4/F Windsor Mansion",
      "street2": "29-31 Chatham Road",
      "street3": null,
      "city": "Tsim Sha Tsui",
      "state": "Kowloon",
      "zip": null,
      "country": "Hong Kong",
      "phone": "+852 2368 8060"
    },
    "destination": {
      "id": 2343,
      "description": "PT. Trisco",
      "street1": "Jl. Raya Kopo - Soreang",
      "street2": "KM. 11.5 Katapang - Soreang",
      "street3": null,
      "city": "Bandung",
      "state": "Jawa Barat",
      "zip": "40971",
      "country": "Indonesia",
      "phone": "+62-22 589 7185"
    },
    "shipment_items": [],
    "fabric_orders": [
      {
        "id": 401508,
        "fabric_id": 83661,
        "garment_id": 1154658,
        "length": "4.5",
        "address_id": 2343,
        "extra_fabric": false,
        "fulfillment_failure": false,
        "shipment_id": 389426,
        "reason": null,
        "created_at": "2020-07-28T07:42:53.000Z",
        "status": "accepted",
        "trinity_fabric_number": "E3-4183661",
        "supplier_fabric_number": "28415-180",
        "description": "Grey Purple Stripe",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/E3-4183661",
        "material_type": "Fabric"
      },
      {
        "id": 401531,
        "fabric_id": 83679,
        "garment_id": 1154867,
        "length": "3.5",
        "address_id": 2343,
        "extra_fabric": false,
        "fulfillment_failure": false,
        "shipment_id": 389426,
        "reason": null,
        "created_at": "2020-07-28T11:59:46.000Z",
        "status": "accepted",
        "trinity_fabric_number": "E3-4183679",
        "supplier_fabric_number": "25919-180",
        "description": "Grey Red Windowpane",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/E3-4183679",
        "material_type": "Fabric"
      },
      {
        "id": 401534,
        "fabric_id": 83666,
        "garment_id": 1154675,
        "length": "5.75",
        "address_id": 2343,
        "extra_fabric": false,
        "fulfillment_failure": false,
        "shipment_id": 389426,
        "reason": null,
        "created_at": "2020-07-28T12:05:09.000Z",
        "status": "accepted",
        "trinity_fabric_number": "E3-4183666",
        "supplier_fabric_number": "28341-180",
        "description": "Grey Blue Stripe",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/E3-4183666",
        "material_type": "Fabric"
      },
      {
        "id": 401678,
        "fabric_id": 83638,
        "garment_id": 1154954,
        "length": "3.75",
        "address_id": 2343,
        "extra_fabric": false,
        "fulfillment_failure": false,
        "shipment_id": 389426,
        "reason": null,
        "created_at": "2020-07-28T17:02:10.000Z",
        "status": "accepted",
        "trinity_fabric_number": "E3-4183638",
        "supplier_fabric_number": "28425-180",
        "description": "Grey Blue Windowpane",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/E3-4183638",
        "material_type": "Fabric"
      },
      {
        "id": 401679,
        "fabric_id": 83740,
        "garment_id": 1154968,
        "length": "1.625",
        "address_id": 2343,
        "extra_fabric": false,
        "fulfillment_failure": false,
        "shipment_id": 389426,
        "reason": null,
        "created_at": "2020-07-28T17:02:10.000Z",
        "status": "accepted",
        "trinity_fabric_number": "E3-4183740",
        "supplier_fabric_number": "25928-180",
        "description": "Navy Solid",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/E3-4183740",
        "material_type": "Fabric"
      },
      {
        "id": 401680,
        "fabric_id": 83744,
        "garment_id": 1154949,
        "length": "4.75",
        "address_id": 2343,
        "extra_fabric": false,
        "fulfillment_failure": false,
        "shipment_id": 389426,
        "reason": null,
        "created_at": "2020-07-28T17:03:35.000Z",
        "status": "accepted",
        "trinity_fabric_number": "E3-4183744",
        "supplier_fabric_number": "28381-180",
        "description": "Burgundy Solid",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/E3-4183744",
        "material_type": "Fabric"
      }
    ]
  }
]
```

### Description

Returns all fabric shipments (shipments which contain fabric orders) for a manufacturer.

### Valid Statuses

| Status   | Description                                            |
| -------- | ------------------------------------------------------ |
| pending  | Shipment has been created, but hasn't been shipped yet |
| transit  | Shipment is currently in route to destination          |
| received | Shipment has been received by factory                  |

### HTTP Request

`GET https://api.trinity-apparel.com/v1/fabric_shipments`

### Query Parameters

| Parameter | Default | Description                                   |
| --------- | ------- | --------------------------------------------- |
| status    | N/A     | Only see fabric shipments in a certain status |

### Other

- Permissions: Only manufacturers can access this route. They can only see shipments being sent to their factory.
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
        "material_type": "Fabric",
        "fabric": {
            "id": 29888,
            "active": true,
            "description": "Antique Golfers",
            "supplier_fabric_number": "360072",
            "trinity_fabric_number": "L6-3129888",
            "url": "https://s7d4.scene7.com/is/image/trinityapparel/L6-3129888",
            "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=L6-3129888&res=300",
            "pattern_id": null,
            "weave_id": null,
            "price_tier": 4,
            "discount": null,
            "has_image": true,
            "favorite_id": null,
            "fabric_type": null,
            "fabric_garment_type": 0,
            "trim_garment_type": 759,
            "material_type": "Fabric"
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
        "material_type": "Fabric",
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

_Note_: Almost all fabric orders are generated at checkout. We rarely add them manually to the system. Sometimes a fabric order will be cancelled (typically when the fabric is out of stock) and a new one will be made when the order is edited and a new fabric is chosen.

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
    "description": "White Solid Linen",
    "supplier_fabric_number": "JT 82099-82",
    "trinity_fabric_number": "N6-4072898",
    "url": "https://s7d4.scene7.com/is/image/trinityapparel/N6-4072898",
    "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N6-4072898&res=300",
    "pattern_id": 1,
    "weave_id": null,
    "price_tier": 2,
    "discount": null,
    "has_image": true,
    "favorite_id": null,
    "fabric_type": null,
    "fabric_garment_type": 8,
    "trim_garment_type": 0,
    "material_type": "Fabric"
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

_Note_: Almost all fabric orders are generated at checkout. We rarely add them manually to the system. Sometimes a fabric order will be cancelled (typically when the fabric is out of stock) and a new one will be made when the order is edited and a new fabric is chosen.

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

If the pattern is solid, you will only need to pass the `cuttable_width`, `cuttable_length` and `fabric_type_code` params. If the pattern is stripe or check, you will also need to include the `fabric_type_width`. If the pattern is check, you will also need `fabric_type_length`.

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

## Accept CMT Fabric

```shell
curl -X POST "https://api.trinity-apparel.com/v1/garment_fabrics/:id/accept"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
  "id": 302261,
  "create_date": "2020-11-11T18:53:42.000Z",
  "garment_fabric_id": 24932183,
  "fabric_id": 1,
  "cuttable_width": 120.0,
  "cuttable_length": 140.0,
  "fabric_type": "Solid, Paisley or Other",
  "fabric_type_length": null,
  "fabric_type_width": null,
  "option_id": null
}
```

### Description

Once a CMT fabric has been received and has passed your inspection process, use this API call to mark it as `accepted` and to confirm the length and width of the fabric you received. We use this information to ensure that the CMT fabric was cut to the correct dimensions.

This will create a Fabric Checkpoint and also move the garment to the `Ready` order status (as long as all required fabrics have been received). If unsuccessful, it will return the error that was encountered. If successful, it will return the Fabric Checkpoint.

If the pattern is solid, you will only need to pass the `cuttable_width`, `cuttable_length` and `fabric_type_code` params. If the pattern is stripe or check, you will also need to include the `fabric_type_width`. If the pattern is check, you will also need `fabric_type_length`.

### Detail

The allowed fabric type codes are:

| Code             | Description             |
| ---------------- | ----------------------- |
| check            | Check 1 - Symmetric     |
| check_asymmetric | Check 2 - Asymmetric    |
| solid            | Solid, Paisley or Other |
| stripe           | Stripe                  |

### HTTP Request

`POST https://api.trinity-apparel.com/v1/garment_fabrics/:id/accept`

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

## Reject CMT Fabric

```shell
curl -X POST "https://api.trinity-apparel.com/v1/garment_fabrics/:id/reject"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1176246,
  "title": "IDUK-1176246",
  "order_id": 542524,
  "copied_garment_id": null,
  "price": "184.0",
  "option_cost": "0.0",
  "garment_type": "CCP",
  "created_at": "2020-11-05T04:29:32.000Z",
  "updated_at": null,
  "order_status_id": 21,
  "delay_status_id": 4,
  "fabric_url": "https://s7d4.scene7.com/is/image/trinityapparel/CMT-70001",
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
    "id": 542524,
    "title": "DO-542524",
    "custom_order_number": "Adam Uniform",
    "garment_count": 1,
    "ship_type": "Ground",
    "ship_cost": "8.05",
    "subtotal": "184.0",
    "dealer_discount": "0.0",
    "total_discount": "55.2",
    "tax": "27.37",
    "grand_total": "164.22",
    "deposit_percentage": 100,
    "current_balance": "0.0",
    "measurement_units": "uscust",
    "payment_status": "paid",
    "ordered_at": "2020-11-05T05:01:29.000Z",
    "created_at": "2020-11-05T04:22:07.000Z",
    "invoiced_at": null
  }
}
```

### Description

Use this API call after you receive a CMT fabric and the fabric fails your inspection process. You'll mark the reason it was rejected and this will move the garment into the correct delay status (typically no delay) and notify the Trinity team that the CMT fabric was rejected so they can reach out to the dealer.

If everything was successful, you will get the garment back with the updated order and delay status. If there was an error, the error message will be returned.

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

`POST https://api.trinity-apparel.com/v1/garment_fabrics/:id/reject`

### Query Parameters

| Parameter   | Default | Description                                  |
| ----------- | ------- | -------------------------------------------- |
| id          | N/A     | The specific fabric order you want to reject |
| reason_code | N/A     | The reason you are rejecting the fabric      |

### Other

- Permissions: Only manufacturers can access this route. They can only see garments made at their factory.
- Pagination: No
