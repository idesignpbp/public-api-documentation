# Orders API

## Order Statuses

All garments are in a particular order statuses.  While a garment is being produced it flows through a number of different statuses. Here is a list of all possible status codes:

Status Code | Description
---------- | -------
INCOMPLETE | Incomplete
SUBMITTED | Ready
PENDING | Blue Pencil
PRODUCTION | Production
MADE | Production Complete
SHIPDC | International Transit
INSPECTDC | Final Inspection
SHIPCUST | Delivery
FABHOLD | Fabric Hold
PACKDC | Shipment Processing
SHIPDIRECT | Direct Ship
CANCEL | Canceled
CMTHOLD | CMT Fabric Hold


## Delay Statuses

Sometimes a garment gets delayed during production. We categorize the reason for the delay in an effort to speed up the process. Here is a list of all possible delay codes:

Delay Code | Description
---------- | -------
OK | Not Delayed
FABRIC_OUT | Fabric Out
FABRIC_RECEIPT | Fabric Receipt Delay
FABRIC_DAMAGED | Fabric Flawed/Damaged
FABRIC_SHORT | Fabric Short
DEALER_INSTRUCT | Dealer Instruction Required
GARMENT_DAMAGED | Garment Damaged Delay
TRINITY_REVIEW | Trinity Review
DEALER_HOLD | Dealer Hold
CMT_SHELL | CMT Shell Fabric Delay
CMT_LINING | CMT Lining Fabric Delay
CMT_TRIM | CMT Trim Fabric Delay
PATTERN_REVIEW | Pattern Review
FACTORY_REVIEW | ID Review

## Order Resources

The Orders API returns order, garment, order status, and delay status objects.  These objects can also return these subresources: dealer, customer, currency, address, etc

### Order

```json
# Standard Object - Used in a resource collection
{
    "id": 399780,
    "title": "DO-399780",
    "custom_order_number": null,
    "garment_count": 7,
    "ship_type": "In-Store Pick-Up",
    "ship_cost": "0.0",
    "subtotal": "2554.0",
    "dealer_discount": "0.0",
    "total_discount": "0.0",
    "tax": "0.0",
    "grand_total": "2554.0",
    "deposit_percentage": 50,
    "current_balance": "2554.0",
    "measurement_units": "uscust",
    "payment_status": "offline",
    "ordered_at": "2018-06-29T10:55:15.000Z",
    "created_at": "2018-06-29T09:42:51.000Z",
    "invoiced_at": null,
    "currency": ...,
}
```

Standard Attributes

Attribute | Type | Description
---------- | ------- | -------
id | string | Unique identifier for the object
title | string | Our SKU field which includes the order id number and information about where the factory will send the garment
custom_order_number | string | Dealers can set this field to whatever they want.  It is typically the dealer's SKU or a summary of the order
garment_count | integer | How many garments are in the order. multi-piece garments (e.g., Suit) are counted as 1.
ship_type | string | How is the garment shipped to the final destination
ship_cost | decimal | How much did it cost to ship the whole order
subtotal | decimal | Order amount before tax and discounts are included
dealer_discount | decimal | *Description TBD*
total_discount | decimal | Dollar total of all discounts applied to the order
tax | decimal | Dollar total for taxes on the order
grand_total | decimal | Dollar total for the whole order. Used as a basis for credit card charges and invoices.
deposit_percentage | integer | The percentage of the grand total that must be paid before the order enters production. A number between 0 and 100. The final amount is typically paid after it is made and before it ships to the final destination.
current_balance | decimal | The dollar amount remaining to be paid on the order
measurement_units | string | Units can be `uscust` for US customary units (in) or `si` for metric units (cm)
payment_status | string | an indication if the order has been paid for
ordered_at | datetime | Time that the dealer completed the checkout process and officially placed the order
created_at | datetime | Time when the dealer first began adding garments to the order
invoiced_at | datetime | Time of the first invoice
currency | subresource | currency used in the order


```json
{
    "id": 399780,
    "title": "DO-399780",
    "custom_order_number": null,
    "garment_count": 7,
    "ship_type": "In-Store Pick-Up",
    "ship_cost": "0.0",
    "subtotal": "2554.0",
    "dealer_discount": "0.0",
    "total_discount": "0.0",
    "tax": "0.0",
    "grand_total": "2554.0",
    "deposit_percentage": 50,
    "current_balance": "2554.0",
    "measurement_units": "uscust",
    "payment_status": "offline",
    "ordered_at": "2018-06-29T10:55:15.000Z",
    "created_at": "2018-06-29T09:42:51.000Z",
    "invoiced_at": null,
    "order_type": "MTM",
    "order_source": "workflo",
    "currency": ...,
    "shipping_address": ...,
    "factory_address": ...,
    "dealer": ...,
    "customer": ...,
    "garments": [ ... ]
}
```

Extended Attributes

Attribute | Type | Description
---------- | ------- | -------
order_type | string | `MTM`, `Inventory`, or `MTO` (future)
order_source | string | What system was used to place the order? `workflo` or `studio`
shipping_address | subresource | address of the final destination
factory_address | subresource | address where it was made
dealer | subresource | dealer who placed the order
customer | subresource | person who will wear the clothes
garments | array | array of garments included in the order


## Get All Orders (DOs)

```shell
curl "https://api.trinity-apparel.com/v1/orders"
  -H "AUTHENTICATION Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 299151,
        "title": "DO-299151",
        "custom_order_number": null,
        "garment_count": 1,
        "ship_type": "Ground",
        "ship_cost": "9.0",
        "subtotal": "40.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "49.0",
        "deposit_percentage": 100,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-19T20:12:47.000Z",
        "created_at": "2017-01-19T20:09:41.000Z",
        "invoiced_at": null,
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299152,
        "title": "DO-299152",
        "custom_order_number": "RD-01",
        "garment_count": 2,
        "ship_type": "Ground",
        "ship_cost": "22.0",
        "subtotal": "1076.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "1098.0",
        "deposit_percentage": 50,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-23T15:29:46.000Z",
        "created_at": "2017-01-19T20:20:00.000Z",
        "invoiced_at": "2017-03-15T12:46:50.000Z",
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299153,
        "title": "DO-299153",
        "custom_order_number": null,
        "garment_count": 1,
        "ship_type": "Ground",
        "ship_cost": "9.0",
        "subtotal": "44.5",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "53.5",
        "deposit_percentage": 50,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-19T20:46:22.000Z",
        "created_at": "2017-01-19T20:38:30.000Z",
        "invoiced_at": null,
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299154,
        "title": "DO-299154",
        "custom_order_number": null,
        "garment_count": 9,
        "ship_type": "Ground",
        "ship_cost": "33.0",
        "subtotal": "1492.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "1525.0",
        "deposit_percentage": 50,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-19T21:17:47.000Z",
        "created_at": "2017-01-19T20:38:56.000Z",
        "invoiced_at": "2017-02-23T13:10:05.000Z",
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299155,
        "title": "DO-299155",
        "custom_order_number": null,
        "garment_count": 2,
        "ship_type": "Ground",
        "ship_cost": "14.0",
        "subtotal": "634.4",
        "dealer_discount": "34.2",
        "total_discount": "34.2",
        "tax": "122.84",
        "grand_total": "737.04",
        "deposit_percentage": 0,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-19T22:21:46.000Z",
        "created_at": "2017-01-19T21:26:00.000Z",
        "invoiced_at": null,
        "currency": {
            "name": "GBP",
            "symbol": "£",
            "rate": "0.625"
        }
    },
    {
        "id": 299156,
        "title": "DO-299156",
        "custom_order_number": null,
        "garment_count": 2,
        "ship_type": "Ground",
        "ship_cost": "22.0",
        "subtotal": "633.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "655.0",
        "deposit_percentage": 100,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-19T22:39:03.000Z",
        "created_at": "2017-01-19T22:15:27.000Z",
        "invoiced_at": null,
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299157,
        "title": "DO-299157",
        "custom_order_number": null,
        "garment_count": 1,
        "ship_type": "Ground",
        "ship_cost": "11.0",
        "subtotal": "449.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "460.0",
        "deposit_percentage": 50,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-27T01:51:46.000Z",
        "created_at": "2017-01-20T01:13:25.000Z",
        "invoiced_at": "2017-02-28T11:35:25.000Z",
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299158,
        "title": "DO-299158",
        "custom_order_number": "2262rm",
        "garment_count": 2,
        "ship_type": "Ground",
        "ship_cost": "6.0",
        "subtotal": "80.0",
        "dealer_discount": "4.0",
        "total_discount": "4.0",
        "tax": "16.4",
        "grand_total": "98.4",
        "deposit_percentage": 0,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-20T07:03:09.000Z",
        "created_at": "2017-01-20T07:00:53.000Z",
        "invoiced_at": "2017-02-15T08:54:48.000Z",
        "currency": {
            "name": "GBP",
            "symbol": "£",
            "rate": "0.625"
        }
    },
    {
        "id": 299160,
        "title": "DO-299160",
        "custom_order_number": "Cousin Order",
        "garment_count": 2,
        "ship_type": "Ground",
        "ship_cost": "33.0",
        "subtotal": "1678.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "1711.0",
        "deposit_percentage": 100,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-03-01T13:13:07.000Z",
        "created_at": "2017-01-20T07:27:04.000Z",
        "invoiced_at": null,
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299164,
        "title": "DO-299164",
        "custom_order_number": null,
        "garment_count": 1,
        "ship_type": "Ground",
        "ship_cost": "11.0",
        "subtotal": "519.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "530.0",
        "deposit_percentage": 50,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-20T07:58:40.000Z",
        "created_at": "2017-01-20T07:51:25.000Z",
        "invoiced_at": "2017-02-15T13:37:10.000Z",
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299165,
        "title": "DO-299165",
        "custom_order_number": null,
        "garment_count": 1,
        "ship_type": "Ground",
        "ship_cost": "9.0",
        "subtotal": "75.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "84.0",
        "deposit_percentage": 50,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-20T08:03:29.000Z",
        "created_at": "2017-01-20T07:59:46.000Z",
        "invoiced_at": null,
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299166,
        "title": "DO-299166",
        "custom_order_number": null,
        "garment_count": 4,
        "ship_type": "Ground",
        "ship_cost": "22.0",
        "subtotal": "493.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "515.0",
        "deposit_percentage": 50,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-20T08:40:46.000Z",
        "created_at": "2017-01-20T08:11:03.000Z",
        "invoiced_at": "2017-02-20T10:46:29.000Z",
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299167,
        "title": "DO-299167",
        "custom_order_number": "3898 Rothfeldt",
        "garment_count": 1,
        "ship_type": "Ground",
        "ship_cost": "9.0",
        "subtotal": "59.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "68.0",
        "deposit_percentage": 100,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-20T08:33:36.000Z",
        "created_at": "2017-01-20T08:28:17.000Z",
        "invoiced_at": null,
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299168,
        "title": "DO-299168",
        "custom_order_number": null,
        "garment_count": 1,
        "ship_type": "Ground",
        "ship_cost": "6.0",
        "subtotal": "43.25",
        "dealer_discount": "2.16",
        "total_discount": "2.16",
        "tax": "9.42",
        "grand_total": "56.51",
        "deposit_percentage": 0,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-20T11:28:44.000Z",
        "created_at": "2017-01-20T08:46:28.000Z",
        "invoiced_at": "2017-02-15T08:54:49.000Z",
        "currency": {
            "name": "GBP",
            "symbol": "£",
            "rate": "0.625"
        }
    },
    {
        "id": 299169,
        "title": "DO-299169",
        "custom_order_number": null,
        "garment_count": 1,
        "ship_type": "Ground",
        "ship_cost": "9.0",
        "subtotal": "344.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "353.0",
        "deposit_percentage": 100,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-20T08:53:36.000Z",
        "created_at": "2017-01-20T08:50:18.000Z",
        "invoiced_at": null,
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299170,
        "title": "DO-299170",
        "custom_order_number": "Q2656",
        "garment_count": 6,
        "ship_type": "Ground",
        "ship_cost": "22.0",
        "subtotal": "354.0",
        "dealer_discount": "28.32",
        "total_discount": "28.32",
        "tax": "0.0",
        "grand_total": "347.68",
        "deposit_percentage": 50,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-20T09:28:35.000Z",
        "created_at": "2017-01-20T08:58:54.000Z",
        "invoiced_at": "2017-02-22T10:00:28.000Z",
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299172,
        "title": "DO-299172",
        "custom_order_number": "1181517/Daub/LA",
        "garment_count": 2,
        "ship_type": "Ground",
        "ship_cost": "22.0",
        "subtotal": "499.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "521.0",
        "deposit_percentage": 50,
        "current_balance": "521.0",
        "measurement_units": "uscust",
        "payment_status": "offline",
        "ordered_at": "2017-01-20T09:36:22.000Z",
        "created_at": "2017-01-20T09:05:57.000Z",
        "invoiced_at": null,
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299173,
        "title": "DO-299173",
        "custom_order_number": "3899 Mayberry",
        "garment_count": 2,
        "ship_type": "Ground",
        "ship_cost": "22.0",
        "subtotal": "419.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "441.0",
        "deposit_percentage": 100,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-20T09:35:31.000Z",
        "created_at": "2017-01-20T09:06:19.000Z",
        "invoiced_at": null,
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299174,
        "title": "DO-299174",
        "custom_order_number": "2370",
        "garment_count": 1,
        "ship_type": "Ground",
        "ship_cost": "7.0",
        "subtotal": "266.0",
        "dealer_discount": "13.3",
        "total_discount": "114.38",
        "tax": "31.72",
        "grand_total": "190.34",
        "deposit_percentage": 0,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-20T09:20:58.000Z",
        "created_at": "2017-01-20T09:14:48.000Z",
        "invoiced_at": "2017-03-01T08:56:14.000Z",
        "currency": {
            "name": "GBP",
            "symbol": "£",
            "rate": "0.625"
        }
    },
    {
        "id": 299175,
        "title": "DO-299175",
        "custom_order_number": null,
        "garment_count": 3,
        "ship_type": "Ground",
        "ship_cost": "11.0",
        "subtotal": "242.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "253.0",
        "deposit_percentage": 100,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-20T09:39:03.000Z",
        "created_at": "2017-01-20T09:16:31.000Z",
        "invoiced_at": null,
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299176,
        "title": "DO-299176",
        "custom_order_number": "1181147/Nianick/HP",
        "garment_count": 4,
        "ship_type": "Ground",
        "ship_cost": "11.0",
        "subtotal": "274.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "285.0",
        "deposit_percentage": 50,
        "current_balance": "285.0",
        "measurement_units": "uscust",
        "payment_status": "offline",
        "ordered_at": "2017-01-20T09:57:49.000Z",
        "created_at": "2017-01-20T09:17:31.000Z",
        "invoiced_at": null,
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299177,
        "title": "DO-299177",
        "custom_order_number": "2369",
        "garment_count": 2,
        "ship_type": "Ground",
        "ship_cost": "14.0",
        "subtotal": "570.15",
        "dealer_discount": "28.51",
        "total_discount": "28.51",
        "tax": "111.13",
        "grand_total": "666.77",
        "deposit_percentage": 0,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-20T09:37:29.000Z",
        "created_at": "2017-01-20T09:23:16.000Z",
        "invoiced_at": "2017-03-08T10:26:26.000Z",
        "currency": {
            "name": "GBP",
            "symbol": "£",
            "rate": "0.625"
        }
    },
    {
        "id": 299178,
        "title": "DO-299178",
        "custom_order_number": "0000008",
        "garment_count": 4,
        "ship_type": "Ground",
        "ship_cost": "22.0",
        "subtotal": "424.5",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "446.5",
        "deposit_percentage": 50,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-01-27T14:55:00.000Z",
        "created_at": "2017-01-20T09:25:54.000Z",
        "invoiced_at": "2017-03-23T16:08:40.000Z",
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299180,
        "title": "DO-299180",
        "custom_order_number": "1181502/Moramarco/DC",
        "garment_count": 1,
        "ship_type": "Ground",
        "ship_cost": "11.0",
        "subtotal": "494.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "505.0",
        "deposit_percentage": 50,
        "current_balance": "505.0",
        "measurement_units": "uscust",
        "payment_status": "offline",
        "ordered_at": "2017-01-20T09:40:38.000Z",
        "created_at": "2017-01-20T09:33:01.000Z",
        "invoiced_at": null,
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    },
    {
        "id": 299181,
        "title": "DO-299181",
        "custom_order_number": null,
        "garment_count": 1,
        "ship_type": "Ground",
        "ship_cost": "11.0",
        "subtotal": "379.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "390.0",
        "deposit_percentage": 50,
        "current_balance": "0.0",
        "measurement_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2017-03-22T10:08:45.000Z",
        "created_at": "2017-01-20T09:33:08.000Z",
        "invoiced_at": "2017-04-14T13:37:27.000Z",
        "currency": {
            "name": "USD",
            "symbol": "$",
            "rate": "1.0"
        }
    }
]
```

Returns an array of dealer orders (DOs).

### HTTP Request

`GET https://api.trinity-apparel.com/v1/orders`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
is_active | true | If set to true, the result will only include active fabrics

### Other

- Permissions: All
- Pagination: Yes

## Get a Specific Order

```shell
curl "https://api.trinity-apparel.com/v1/orders/399780"
  -H "AUTHENTICATION Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
    "id": 399780,
    "title": "DO-399780",
    "custom_order_number": null,
    "garment_count": 7,
    "ship_type": "In-Store Pick-Up",
    "ship_cost": "0.0",
    "subtotal": "2554.0",
    "dealer_discount": "0.0",
    "total_discount": "0.0",
    "tax": "0.0",
    "grand_total": "2554.0",
    "deposit_percentage": 50,
    "current_balance": "2554.0",
    "measurement_units": "uscust",
    "payment_status": "offline",
    "ordered_at": "2018-06-29T10:55:15.000Z",
    "created_at": "2018-06-29T09:42:51.000Z",
    "invoiced_at": null,
    "order_type": "MTM",
    "order_source": "workflo",
    "currency": {
        "name": "USD",
        "symbol": "$",
        "rate": "1.0"
    },
    "shipping_address": {
        "id": 1477,
        "description": "Trinity",
        "street1": "193 Business Park Dr",
        "street2": null,
        "street3": null,
        "city": "Ridgeland",
        "state": "MS",
        "zip": "39157",
        "country": "USA",
        "phone": null
    },
    "factory_address": {
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
    "dealer": {
        "id": 1106,
        "name": "Studio Garments",
        "first_name": "Studio",
        "last_name": "Garments",
        "company_name": null,
        "email": "jwiggins@idpbp.com",
        "phone": "6017132628",
        "country": "USA"
    },
    "customer": {
        "id": 87285,
        "created_at": "2016-05-29T15:08:38.000Z",
        "name": "Mr Mannequin",
        "first_name": "Mr",
        "last_name": "Mannequin",
        "email": null
    },
    "garments": [
        {
            "id": 872898,
            "title": "ID-872898",
            "order_id": 399780,
            "copied_garment_id": null,
            "garment_price": "274.0",
            "option_cost": "65.0",
            "garment_type": "CSC",
            "factory_prefix": "ID",
            "factory_index": "1/7",
            "created_at": "2018-06-29T09:44:15.000Z",
            "updated_at": "2018-08-03T04:01:21.000Z"
        },
        {
            "id": 872909,
            "title": "ID-872909",
            "order_id": 399780,
            "copied_garment_id": 872898,
            "garment_price": "274.0",
            "option_cost": "65.0",
            "garment_type": "CSC",
            "factory_prefix": "ID",
            "factory_index": "2/7",
            "created_at": "2018-06-29T10:02:12.000Z",
            "updated_at": "2018-07-27T03:35:22.000Z"
        },
        {
            "id": 872918,
            "title": "ID-872918",
            "order_id": 399780,
            "copied_garment_id": 872909,
            "garment_price": "274.0",
            "option_cost": "65.0",
            "garment_type": "CSC",
            "factory_prefix": "ID",
            "factory_index": "3/7",
            "created_at": "2018-06-29T10:20:23.000Z",
            "updated_at": "2018-07-25T04:05:58.000Z"
        },
        {
            "id": 872919,
            "title": "ID-872919",
            "order_id": 399780,
            "copied_garment_id": 872898,
            "garment_price": "274.0",
            "option_cost": "65.0",
            "garment_type": "CSC",
            "factory_prefix": "ID",
            "factory_index": "4/7",
            "created_at": "2018-06-29T10:26:58.000Z",
            "updated_at": "2018-07-23T03:51:47.000Z"
        },
        {
            "id": 872920,
            "title": "ID-872920",
            "order_id": 399780,
            "copied_garment_id": 872918,
            "garment_price": "460.0",
            "option_cost": "60.0",
            "garment_type": "CSC",
            "factory_prefix": "ID",
            "factory_index": "5/7",
            "created_at": "2018-06-29T10:30:15.000Z",
            "updated_at": "2018-07-26T03:38:01.000Z"
        },
        {
            "id": 872932,
            "title": "ID-872932",
            "order_id": 399780,
            "copied_garment_id": 872920,
            "garment_price": "274.0",
            "option_cost": "65.0",
            "garment_type": "CSC",
            "factory_prefix": "ID",
            "factory_index": "6/7",
            "created_at": "2018-06-29T10:45:08.000Z",
            "updated_at": "2018-07-23T03:51:40.000Z"
        },
        {
            "id": 872933,
            "title": "ID-872933",
            "order_id": 399780,
            "copied_garment_id": 872932,
            "garment_price": "274.0",
            "option_cost": "65.0",
            "garment_type": "CSC",
            "factory_prefix": "ID",
            "factory_index": "7/7",
            "created_at": "2018-06-29T10:48:38.000Z",
            "updated_at": "2018-07-23T03:51:45.000Z"
        }
    ]
}
```

Returns details on a specific order and a snapshot of the garments within the order.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/orders/:id`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
id | N/A | The specific order id you want to see

### Other

- Permissions: All
- Pagination: N/A

## Get All Garments

```shell
curl "https://api.trinity-apparel.com/v1/garments"
  -H "AUTHENTICATION Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 824833,
        "title": "ID-824833",
        "order_id": 376598,
        "copied_garment_id": null,
        "garment_price": "370.0",
        "option_cost": "15.0",
        "garment_type": "CSC",
        "factory_prefix": "ID",
        "factory_index": "1/2",
        "created_at": "2018-03-10T15:06:20.000Z",
        "updated_at": "2018-03-28T01:49:39.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 376598,
            "title": "DO-376598",
            "custom_order_num": "Jason Saint Peter",
            "garment_count": 2,
            "ship_type": "Ground",
            "ship_cost": "11.0",
            "subtotal": "450.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "461.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-10T16:17:22.000Z",
            "created_at": "2018-03-09T18:09:23.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 826855,
        "title": "ID-826855",
        "order_id": 377644,
        "copied_garment_id": null,
        "garment_price": "440.0",
        "option_cost": "15.0",
        "garment_type": "CCP",
        "factory_prefix": "ID",
        "factory_index": "1/1",
        "created_at": "2018-03-14T14:49:32.000Z",
        "updated_at": "2018-04-09T02:21:04.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 377644,
            "title": "DO-377644",
            "custom_order_num": "Chris Wilhelm",
            "garment_count": 1,
            "ship_type": "Ground",
            "ship_cost": "11.0",
            "subtotal": "455.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "466.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-14T14:59:03.000Z",
            "created_at": "2018-03-14T14:39:30.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 826936,
        "title": "ID-826936",
        "order_id": 377707,
        "copied_garment_id": null,
        "garment_price": "380.0",
        "option_cost": "5.0",
        "garment_type": "CSC",
        "factory_prefix": "ID",
        "factory_index": "1/2",
        "created_at": "2018-03-14T16:16:04.000Z",
        "updated_at": "2018-04-26T03:24:04.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 377707,
            "title": "DO-377707",
            "custom_order_num": "Roy Fickling",
            "garment_count": 2,
            "ship_type": "Ground",
            "ship_cost": "11.0",
            "subtotal": "565.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "576.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-14T16:31:02.000Z",
            "created_at": "2018-03-14T16:15:24.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 826937,
        "title": "ID-826937",
        "order_id": 377707,
        "copied_garment_id": null,
        "garment_price": "180.0",
        "option_cost": "0.0",
        "garment_type": "CT",
        "factory_prefix": "ID",
        "factory_index": "2/2",
        "created_at": "2018-03-14T16:16:39.000Z",
        "updated_at": "2018-04-08T03:30:17.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 377707,
            "title": "DO-377707",
            "custom_order_num": "Roy Fickling",
            "garment_count": 2,
            "ship_type": "Ground",
            "ship_cost": "11.0",
            "subtotal": "565.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "576.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-14T16:31:02.000Z",
            "created_at": "2018-03-14T16:15:24.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 827028,
        "title": "ID-827028",
        "order_id": 377746,
        "copied_garment_id": null,
        "garment_price": "300.0",
        "option_cost": "5.0",
        "garment_type": "CSC",
        "factory_prefix": "ID",
        "factory_index": "1/4",
        "created_at": "2018-03-14T17:16:57.000Z",
        "updated_at": "2018-04-12T03:36:53.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 377746,
            "title": "DO-377746",
            "custom_order_num": "Alfred Sams",
            "garment_count": 4,
            "ship_type": "Ground",
            "ship_cost": "22.0",
            "subtotal": "825.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "847.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-14T17:45:28.000Z",
            "created_at": "2018-03-14T17:16:21.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 827033,
        "title": "ID-827033",
        "order_id": 377746,
        "copied_garment_id": null,
        "garment_price": "100.0",
        "option_cost": "0.0",
        "garment_type": "CT",
        "factory_prefix": "ID",
        "factory_index": "2/4",
        "created_at": "2018-03-14T17:28:22.000Z",
        "updated_at": "2018-04-16T03:16:09.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 377746,
            "title": "DO-377746",
            "custom_order_num": "Alfred Sams",
            "garment_count": 4,
            "ship_type": "Ground",
            "ship_cost": "22.0",
            "subtotal": "825.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "847.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-14T17:45:28.000Z",
            "created_at": "2018-03-14T17:16:21.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 827043,
        "title": "ID-827043",
        "order_id": 377746,
        "copied_garment_id": 827028,
        "garment_price": "300.0",
        "option_cost": "20.0",
        "garment_type": "CSC",
        "factory_prefix": "ID",
        "factory_index": "3/4",
        "created_at": "2018-03-14T17:40:41.000Z",
        "updated_at": "2018-04-12T03:36:54.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 377746,
            "title": "DO-377746",
            "custom_order_num": "Alfred Sams",
            "garment_count": 4,
            "ship_type": "Ground",
            "ship_cost": "22.0",
            "subtotal": "825.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "847.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-14T17:45:28.000Z",
            "created_at": "2018-03-14T17:16:21.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 827044,
        "title": "ID-827044",
        "order_id": 377746,
        "copied_garment_id": 827033,
        "garment_price": "100.0",
        "option_cost": "0.0",
        "garment_type": "CT",
        "factory_prefix": "ID",
        "factory_index": "4/4",
        "created_at": "2018-03-14T17:41:10.000Z",
        "updated_at": "2018-04-16T03:16:08.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 377746,
            "title": "DO-377746",
            "custom_order_num": "Alfred Sams",
            "garment_count": 4,
            "ship_type": "Ground",
            "ship_cost": "22.0",
            "subtotal": "825.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "847.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-14T17:45:28.000Z",
            "created_at": "2018-03-14T17:16:21.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 827421,
        "title": "ID-827421",
        "order_id": 377919,
        "copied_garment_id": null,
        "garment_price": "370.0",
        "option_cost": "15.0",
        "garment_type": "CSC",
        "factory_prefix": "ID",
        "factory_index": "1/10",
        "created_at": "2018-03-15T12:58:26.000Z",
        "updated_at": "2018-03-31T02:17:14.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 377919,
            "title": "DO-377919",
            "custom_order_num": "Bryan Bennight",
            "garment_count": 10,
            "ship_type": "Ground",
            "ship_cost": "33.0",
            "subtotal": "1541.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "1574.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-15T13:43:24.000Z",
            "created_at": "2018-03-15T12:56:48.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 827429,
        "title": "ID-827429",
        "order_id": 377919,
        "copied_garment_id": null,
        "garment_price": "130.0",
        "option_cost": "0.0",
        "garment_type": "CT",
        "factory_prefix": "ID",
        "factory_index": "2/10",
        "created_at": "2018-03-15T13:06:15.000Z",
        "updated_at": "2018-04-08T03:30:57.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 377919,
            "title": "DO-377919",
            "custom_order_num": "Bryan Bennight",
            "garment_count": 10,
            "ship_type": "Ground",
            "ship_cost": "33.0",
            "subtotal": "1541.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "1574.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-15T13:43:24.000Z",
            "created_at": "2018-03-15T12:56:48.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 827436,
        "title": "ID-827436",
        "order_id": 377919,
        "copied_garment_id": null,
        "garment_price": "530.0",
        "option_cost": "15.0",
        "garment_type": "CCP",
        "factory_prefix": "ID",
        "factory_index": "3/10",
        "created_at": "2018-03-15T13:09:26.000Z",
        "updated_at": "2018-04-08T03:29:08.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 377919,
            "title": "DO-377919",
            "custom_order_num": "Bryan Bennight",
            "garment_count": 10,
            "ship_type": "Ground",
            "ship_cost": "33.0",
            "subtotal": "1541.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "1574.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-15T13:43:24.000Z",
            "created_at": "2018-03-15T12:56:48.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 827660,
        "title": "ID-827660",
        "order_id": 377954,
        "copied_garment_id": null,
        "garment_price": "340.0",
        "option_cost": "15.0",
        "garment_type": "CCP",
        "factory_prefix": "ID",
        "factory_index": "1/1",
        "created_at": "2018-03-15T16:18:01.000Z",
        "updated_at": "2018-04-10T03:00:19.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 377954,
            "title": "DO-377954",
            "custom_order_num": "Thomas Heidrich",
            "garment_count": 1,
            "ship_type": "Ground",
            "ship_cost": "11.0",
            "subtotal": "355.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "366.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-15T16:29:25.000Z",
            "created_at": "2018-03-15T13:51:39.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 827521,
        "title": "ID-827521",
        "order_id": 377967,
        "copied_garment_id": 679524,
        "garment_price": "340.0",
        "option_cost": "15.0",
        "garment_type": "CCP",
        "factory_prefix": "ID",
        "factory_index": "1/5",
        "created_at": "2018-03-15T14:15:45.000Z",
        "updated_at": "2018-04-11T02:35:28.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 377967,
            "title": "DO-377967",
            "custom_order_num": "Ward Stone",
            "garment_count": 5,
            "ship_type": "Ground",
            "ship_cost": "22.0",
            "subtotal": "660.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "682.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-15T14:49:15.000Z",
            "created_at": "2018-03-15T14:12:36.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 827562,
        "title": "ID-827562",
        "order_id": 377991,
        "copied_garment_id": null,
        "garment_price": "340.0",
        "option_cost": "15.0",
        "garment_type": "CCP",
        "factory_prefix": "ID",
        "factory_index": "1/2",
        "created_at": "2018-03-15T14:54:13.000Z",
        "updated_at": "2018-04-19T02:19:12.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 377991,
            "title": "DO-377991",
            "custom_order_num": "Tim Sanders",
            "garment_count": 2,
            "ship_type": "Ground",
            "ship_cost": "22.0",
            "subtotal": "424.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "446.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-15T15:12:34.000Z",
            "created_at": "2018-03-15T14:50:21.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 827694,
        "title": "ID-827694",
        "order_id": 378049,
        "copied_garment_id": 705021,
        "garment_price": "100.0",
        "option_cost": "0.0",
        "garment_type": "CT",
        "factory_prefix": "ID",
        "factory_index": "2/2",
        "created_at": "2018-03-15T17:05:01.000Z",
        "updated_at": "2018-04-11T02:35:36.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 378049,
            "title": "DO-378049",
            "custom_order_num": "Ben Frye",
            "garment_count": 2,
            "ship_type": "Ground",
            "ship_cost": "11.0",
            "subtotal": "165.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "176.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-15T17:09:41.000Z",
            "created_at": "2018-03-15T16:53:21.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 831634,
        "title": "ID-831634",
        "order_id": 379923,
        "copied_garment_id": 628693,
        "garment_price": "340.0",
        "option_cost": "15.0",
        "garment_type": "CSC",
        "factory_prefix": "ID",
        "factory_index": "1/4",
        "created_at": "2018-03-23T15:07:06.000Z",
        "updated_at": "2018-04-27T03:58:24.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 379923,
            "title": "DO-379923",
            "custom_order_num": "Bennett Frye",
            "garment_count": 4,
            "ship_type": "Ground",
            "ship_cost": "22.0",
            "subtotal": "720.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "742.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-26T17:17:38.000Z",
            "created_at": "2018-03-23T15:05:02.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 831639,
        "title": "ID-831639",
        "order_id": 379923,
        "copied_garment_id": 628694,
        "garment_price": "150.0",
        "option_cost": "0.0",
        "garment_type": "CT",
        "factory_prefix": "ID",
        "factory_index": "2/4",
        "created_at": "2018-03-23T15:18:56.000Z",
        "updated_at": "2018-04-19T02:19:46.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 379923,
            "title": "DO-379923",
            "custom_order_num": "Bennett Frye",
            "garment_count": 4,
            "ship_type": "Ground",
            "ship_cost": "22.0",
            "subtotal": "720.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "742.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-26T17:17:38.000Z",
            "created_at": "2018-03-23T15:05:02.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 831640,
        "title": "ID-831640",
        "order_id": 379923,
        "copied_garment_id": 831639,
        "garment_price": "150.0",
        "option_cost": "0.0",
        "garment_type": "CT",
        "factory_prefix": "ID",
        "factory_index": "3/4",
        "created_at": "2018-03-23T15:21:04.000Z",
        "updated_at": "2018-04-23T04:16:45.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 379923,
            "title": "DO-379923",
            "custom_order_num": "Bennett Frye",
            "garment_count": 4,
            "ship_type": "Ground",
            "ship_cost": "22.0",
            "subtotal": "720.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "742.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-26T17:17:38.000Z",
            "created_at": "2018-03-23T15:05:02.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 831667,
        "title": "ID-831667",
        "order_id": 379945,
        "copied_garment_id": 718222,
        "garment_price": "340.0",
        "option_cost": "5.0",
        "garment_type": "CSC",
        "factory_prefix": "ID",
        "factory_index": "1/6",
        "created_at": "2018-03-23T16:07:15.000Z",
        "updated_at": "2018-05-03T05:07:53.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 379945,
            "title": "DO-379945",
            "custom_order_num": "Jack Knox",
            "garment_count": 6,
            "ship_type": "Ground",
            "ship_cost": "33.0",
            "subtotal": "1309.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "1342.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-30T12:12:35.000Z",
            "created_at": "2018-03-23T16:06:08.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 831675,
        "title": "ID-831675",
        "order_id": 379945,
        "copied_garment_id": 831667,
        "garment_price": "460.0",
        "option_cost": "15.0",
        "garment_type": "CSC",
        "factory_prefix": "ID",
        "factory_index": "2/6",
        "created_at": "2018-03-23T16:16:48.000Z",
        "updated_at": "2018-05-03T05:07:53.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 379945,
            "title": "DO-379945",
            "custom_order_num": "Jack Knox",
            "garment_count": 6,
            "ship_type": "Ground",
            "ship_cost": "33.0",
            "subtotal": "1309.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "1342.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-30T12:12:35.000Z",
            "created_at": "2018-03-23T16:06:08.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 832576,
        "title": "ID-832576",
        "order_id": 379945,
        "copied_garment_id": 779828,
        "garment_price": "140.0",
        "option_cost": "0.0",
        "garment_type": "CT",
        "factory_prefix": "ID",
        "factory_index": "3/6",
        "created_at": "2018-03-26T16:50:17.000Z",
        "updated_at": "2018-05-03T05:08:30.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 379945,
            "title": "DO-379945",
            "custom_order_num": "Jack Knox",
            "garment_count": 6,
            "ship_type": "Ground",
            "ship_cost": "33.0",
            "subtotal": "1309.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "1342.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-30T12:12:35.000Z",
            "created_at": "2018-03-23T16:06:08.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 832577,
        "title": "ID-832577",
        "order_id": 379945,
        "copied_garment_id": 832576,
        "garment_price": "200.0",
        "option_cost": "0.0",
        "garment_type": "CT",
        "factory_prefix": "ID",
        "factory_index": "4/6",
        "created_at": "2018-03-26T16:51:59.000Z",
        "updated_at": "2018-04-24T02:44:05.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 379945,
            "title": "DO-379945",
            "custom_order_num": "Jack Knox",
            "garment_count": 6,
            "ship_type": "Ground",
            "ship_cost": "33.0",
            "subtotal": "1309.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "1342.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-30T12:12:35.000Z",
            "created_at": "2018-03-23T16:06:08.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 832686,
        "title": "ID-832686",
        "order_id": 380420,
        "copied_garment_id": null,
        "garment_price": "340.0",
        "option_cost": "15.0",
        "garment_type": "CCP",
        "factory_prefix": "ID",
        "factory_index": "1/6",
        "created_at": "2018-03-26T20:58:17.000Z",
        "updated_at": "2018-05-03T05:08:07.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 380420,
            "title": "DO-380420",
            "custom_order_num": "Robert Minor",
            "garment_count": 6,
            "ship_type": "Ground",
            "ship_cost": "33.0",
            "subtotal": "945.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "978.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-30T12:11:48.000Z",
            "created_at": "2018-03-26T20:57:23.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 832688,
        "title": "ID-832688",
        "order_id": 380420,
        "copied_garment_id": null,
        "garment_price": "300.0",
        "option_cost": "15.0",
        "garment_type": "CSC",
        "factory_prefix": "ID",
        "factory_index": "2/6",
        "created_at": "2018-03-26T21:03:14.000Z",
        "updated_at": "2018-04-25T03:22:11.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 380420,
            "title": "DO-380420",
            "custom_order_num": "Robert Minor",
            "garment_count": 6,
            "ship_type": "Ground",
            "ship_cost": "33.0",
            "subtotal": "945.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "978.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-30T12:11:48.000Z",
            "created_at": "2018-03-26T20:57:23.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 832863,
        "title": "ID-832863",
        "order_id": 380498,
        "copied_garment_id": null,
        "garment_price": "410.0",
        "option_cost": "10.0",
        "garment_type": "CSC",
        "factory_prefix": "ID",
        "factory_index": "1/1",
        "created_at": "2018-03-27T10:14:19.000Z",
        "updated_at": "2018-04-25T03:22:11.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "description": "Delivery",
            "name": "Delivery"
        },
        "delay_status": {
            "id": 1,
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 380498,
            "title": "DO-380498",
            "custom_order_num": "Jim Daws",
            "garment_count": 1,
            "ship_type": "Ground",
            "ship_cost": "11.0",
            "subtotal": "420.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "431.0",
            "deposit_pct": 100,
            "current_balance": "0.0",
            "msmt_units": "uscust",
            "payment_status": "paid",
            "ordered_at": "2018-03-30T13:47:30.000Z",
            "created_at": "2018-03-27T10:06:31.000Z",
            "invoiced_at": null
        }
    }
]
```

Returns an array of garments.  Each garment will have pricing information and order status information.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/garments`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
order_id | N/A | Show garments that are part of a specific dealer order
order_status_code | N/A | Show garments that are in a specific order status
delay_status_code | N/A | Show garments that are in a specific delay status

### Other

- Permissions: All
- Pagination: Yes

## Get a Specific Garment

```shell
curl "https://api.trinity-apparel.com/v1/garments/399780"
  -H "AUTHENTICATION Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
    "id": 861593,
    "title": "ID-861593",
    "order_id": 394366,
    "copied_garment_id": 816718,
    "garment_price": "75.0",
    "option_cost": "0.0",
    "tailoring_grade": 129,
    "copied_suit_id": 816718,
    "portfolio_specific_id": null,
    "last_status_change_date": "2018-06-21T16:04:49.000Z",
    "last_delay_change_date": null,
    "suit_complete": false,
    "garment_type": {
        "description": "CSHT",
        "garment_type": 8,
        "composed_gtype": false
    },
    "factory_prefix": "ID",
    "factory_index": "1/1",
    "created_at": "2018-06-01T12:11:18.000Z",
    "updated_at": "2018-06-13T03:16:04.000Z",
    "manufacturer": {
        "id": 2,
        "address_id": 1943,
        "name": "iD Shirts",
        "email": "info@trinity-apparel.com"
    },
    "fabric": {
        "id": 43569,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "Pink Basket Weave",
        "supplier_fabric_number": "ST 61776-68",
        "trinity_fabric_number": "P3-3643569",
        "url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=P3-3643569",
        "inventory_status": "In Stock"
    },
    "order_status": {
        "code": "SHIPCUST",
        "description": "Delivery",
        "name": "Delivery"
    },
    "dealer_order": {
        "id": 394366,
        "title": "DO-394366",
        "custom_order_num": "Jason Jungberg",
        "garment_count": 1,
        "ship_type": "Ground",
        "ship_cost": "9.0",
        "subtotal": "75.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "84.0",
        "deposit_pct": 100,
        "current_balance": "0.0",
        "msmt_units": "uscust",
        "payment_status": "paid",
        "ordered_at": "2018-06-01T12:45:49.000Z",
        "created_at": "2018-06-01T12:10:42.000Z",
        "invoiced_at": null
    }
}
```

Returns details on a specific garment.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/garments/:id`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
id | N/A | The specific garment id you want to see

### Other

- Permissions: All
- Pagination: N/A

## Get Order Statuses

```shell
curl "https://api.trinity-apparel.com/v1/order_statuses"
  -H "AUTHENTICATION Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "code": "INCOMPLETE",
        "name": "Incomplete",
        "description": "Incomplete"
    },
    {
        "code": "CMTHOLD",
        "name": null,
        "description": "CMT Fabric Hold"
    },
    {
        "code": "FABHOLD",
        "name": "Restocking",
        "description": "Fabric Hold"
    },
    {
        "code": "SUBMITTED",
        "name": "Submitted",
        "description": "Ready"
    },
    {
        "code": "PENDING",
        "name": "Pending",
        "description": "Blue Pencil"
    },
    {
        "code": "PRODUCTION",
        "name": "Production",
        "description": "Production"
    },
    {
        "code": "MADE",
        "name": null,
        "description": "Production Complete"
    },
    {
        "code": "SHIPDC",
        "name": null,
        "description": "International Transit"
    },
    {
        "code": "INSPECTDC",
        "name": null,
        "description": "Final Inspection"
    },
    {
        "code": "PACKDC",
        "name": null,
        "description": "Shipment Processing"
    },
    {
        "code": "SHIPCUST",
        "name": "Delivery",
        "description": "Delivery"
    },
    {
        "code": "SHIPDIRECT",
        "name": null,
        "description": "Direct Ship"
    },
    {
        "code": "CANCEL",
        "name": null,
        "description": "Canceled"
    }
]
```

Returns a list of all order statuses

### HTTP Request

`GET https://api.trinity-apparel.com/v1/order_statuses`

### Query Parameters

None

### Other

- Permissions: All
- Pagination: N/A

## Get an Order Status

```shell
curl "https://api.trinity-apparel.com/v1/order_statuses/FABHOLD"
  -H "AUTHENTICATION Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
    "code": "FABHOLD",
    "name": "Restocking",
    "description": "Fabric Hold",
    "max_delay_days": 9,
    "max_delay_days_shirts": 9,
    "max_delay_days_suits": 9,
    "is_active": true
}
```

Returns details on an order status

### HTTP Request

`GET https://api.trinity-apparel.com/v1/order_statuses/:code`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
code | N/A | The specific order status code

### Other

- Permissions: All
- Pagination: N/A

## Get Delay Statuses

```shell
curl "https://api.trinity-apparel.com/v1/delay_statuses"
  -H "AUTHENTICATION Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "code": "OK",
        "description": "Not Delayed"
    },
    {
        "code": "FABRIC_OUT",
        "description": "Fabric Out"
    },
    {
        "code": "FABRIC_RECEIPT",
        "description": "Fabric Receipt Delay"
    },
    {
        "code": "FABRIC_DAMAGED",
        "description": "Fabric Flawed/Damaged"
    },
    {
        "code": "FABRIC_SHORT",
        "description": "Fabric Short"
    },
    {
        "code": "DEALER_INSTRUCT",
        "description": "Dealer Instruction Required"
    },
    {
        "code": "GARMENT_DAMAGED",
        "description": "Garment Damaged Delay"
    },
    {
        "code": "TRINITY_REVIEW",
        "description": "Trinity Review"
    },
    {
        "code": "DEALER_HOLD",
        "description": "Dealer Hold"
    },
    {
        "code": "CMT_SHELL",
        "description": "CMT Shell Fabric Delay"
    },
    {
        "code": "CMT_LINING",
        "description": "CMT Lining Fabric Delay"
    },
    {
        "code": "CMT_TRIM",
        "description": "CMT Trim Fabric Delay"
    },
    {
        "code": "PATTERN_REVIEW",
        "description": "Pattern Review"
    },
    {
        "code": "FACTORY_REVIEW",
        "description": "ID Review"
    }
]
```

Returns a list of all delay statuses

### HTTP Request

`GET https://api.trinity-apparel.com/v1/delay_statuses`

### Query Parameters

None

### Other

- Permissions: All
- Pagination: N/A

## Get a Delay Status

```shell
curl "https://api.trinity-apparel.com/v1/delay_statuses/FABRIC_OUT"
  -H "AUTHENTICATION Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
    "code": "FABRIC_OUT",
    "description": "Fabric Out"
}
```

Returns details on a delay status. It doesn't provide that much information, as you can see.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/delay_statuses/:code`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
code | N/A | The specific delay status code

### Other

- Permissions: All
- Pagination: N/A