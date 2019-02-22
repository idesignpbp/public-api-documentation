# Orders API

## Order Statuses

All garments are in a particular order statuses.  While a garment is being produced it flows through a number of different statuses. Here is a list of all possible status codes:

| Status Code | Description           |
| ----------- | --------------------- |
| INCOMPLETE  | Incomplete            |
| SUBMITTED   | Ready                 |
| PENDING     | Blue Pencil           |
| PRODUCTION  | Production            |
| MADE        | Production Complete   |
| SHIPDC      | International Transit |
| INSPECTDC   | Final Inspection      |
| SHIPCUST    | Delivery              |
| FABHOLD     | Fabric Hold           |
| PACKDC      | Shipment Processing   |
| SHIPDIRECT  | Direct Ship           |
| CANCEL      | Canceled              |
| CMTHOLD     | CMT Fabric Hold       |

## Delay Statuses

Sometimes a garment gets delayed during production. We categorize the reason for the delay in an effort to speed up the process. Here is a list of all possible delay codes:

| Delay Code      | Description                 |
| --------------- | --------------------------- |
| OK              | Not Delayed                 |
| FABRIC_OUT      | Fabric Out                  |
| FABRIC_RECEIPT  | Fabric Receipt Delay        |
| FABRIC_DAMAGED  | Fabric Flawed/Damaged       |
| FABRIC_SHORT    | Fabric Short                |
| DEALER_INSTRUCT | Dealer Instruction Required |
| GARMENT_DAMAGED | Garment Damaged Delay       |
| TRINITY_REVIEW  | Trinity Review              |
| DEALER_HOLD     | Dealer Hold                 |
| CMT_SHELL       | CMT Shell Fabric Delay      |
| CMT_LINING      | CMT Lining Fabric Delay     |
| CMT_TRIM        | CMT Trim Fabric Delay       |
| PATTERN_REVIEW  | Pattern Review              |
| FACTORY_REVIEW  | ID Review                   |

## Garment Types

Description of what the different garment type codes mean:

| Garment Type | Description             |
| ------------ | ----------------------- |
| CSC          | Coat                    |
| CV           | Vest                    |
| CT           | Pant                    |
| CCP          | Coat & Pant             |
| CCVP         | Coat, Vest & Pant       |
| CSHT         | Shirt                   |
| CCPP         | Coat, Pant, & Pant      |
| CCVPP        | Coat, Vest, Pant & Pant |
| CTOPC        | Topcoat                 |
| CSHO         | Short                   |
| CBK          | Breek                   |
| TIE          | Tie                     |
| SWK          | Swacket                 |

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

| Attribute                                    | Description                                                                                                                                                                                                           |
| -------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id <br> <span>string</span>                  | Unique identifier for the object                                                                                                                                                                                      |
| title <br> <span>string</span>               | Our SKU field for orders                                                                                                                                                                                              |
| custom_order_number <br> <span>string</span> | Dealers can set this field to whatever they want.  It is typically the dealer's SKU or a summary of the order                                                                                                         |
| garment_count <br> <span>integer</span>      | How many garments are in the order. multi-piece garments (e.g., Suit) are counted as 1.                                                                                                                               |
| ship_type <br> <span>string</span>           | How is the garment shipped to the final destination                                                                                                                                                                   |
| ship_cost <br> <span>decimal</span>          | How much did it cost to ship the whole order                                                                                                                                                                          |
| subtotal <br> <span>decimal</span>           | Order amount before tax and discounts are included                                                                                                                                                                    |
| dealer_discount <br> <span>decimal</span>    | Dealer discount is the amount of dealer's permanent discounts                                                                                                                                                         |
| total_discount <br> <span>decimal</span>     | Dollar total of all discounts applied to the order                                                                                                                                                                    |
| tax <br> <span>decimal</span>                | Dollar total for taxes on the order                                                                                                                                                                                   |
| grand_total <br> <span>decimal</span>        | Dollar total for the whole order. Used as a basis for credit card charges and invoices.                                                                                                                               |
| deposit_percentage <br> <span>integer</span> | The percentage of the grand total that must be paid before the order enters production. A number between 0 and 100. The final amount is typically paid after it is made and before it ships to the final destination. |
| current_balance <br> <span>decimal</span>    | The dollar amount remaining to be paid on the order                                                                                                                                                                   |
| measurement_units <br> <span>string</span>   | Units can be `uscust` for US customary units (in) or `si` for metric units (cm)                                                                                                                                       |
| payment_status <br> <span>string</span>      | An indication if the order has been paid for                                                                                                                                                                          |
| ordered_at <br> <span>datetime</span>        | Time that the dealer completed the checkout process and officially placed the order                                                                                                                                   |
| created_at <br> <span>datetime</span>        | Time when the dealer first began adding garments to the order                                                                                                                                                         |
| invoiced_at <br> <span>datetime</span>       | Time of the first invoice                                                                                                                                                                                             |
| currency <br> <span>subresource</span>       | Currency used in the order                                                                                                                                                                                            |


```json
# Extended Object
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

| Attribute                                      | Description                                                    |
| ---------------------------------------------- | -------------------------------------------------------------- |
| order_type <br> <span>string</span>            | `MTM`, `Inventory`, or `MTO` (future)                          |
| order_source <br> <span>string</span>          | What system was used to place the order? `workflo` or `studio` |
| shipping_address <br> <span>subresource</span> | Address of the final destination                               |
| factory_address <br> <span>subresource</span>  | Address where it was made                                      |
| dealer <br> <span>subresource</span>           | Dealer who placed the order                                    |
| customer <br> <span>subresource</span>         | Person who will wear the garments                              |
| garments <br> <span>array</span>               | Array of garments included in the order                        |

### Currency

```json
# Standard Object - Used in a resource collection
{
    "name": "USD",
    "symbol": "$",
    "rate": "1.0"
}
```

Standard Attributes

| Attribute                       | Description             |
| ------------------------------- | ----------------------- |
| name <br> <span>string</span>   | Type of currency used   |
| symbol <br> <span>string</span> | Symbol of currency used |
| rate <br> <span>string</span>   | *Description TBD*       |

### Shipping Address

```json
# Standard Object - Used in a resource collection
{
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
}
```

Standard Attributes

| Attribute                            | Description                      |
| ------------------------------------ | -------------------------------- |
| id <br> <span>integer</span>         | Unique identifier for the object |
| description <br> <span>string</span> | Brief description of address     |
| street1 <br> <span>string</span>     | First street line of address     |
| street2 <br> <span>string</span>     | Second street line of address    |
| street3 <br> <span>string</span>     | Third street line of address     |
| city <br> <span>string</span>        | City for the address             |
| state <br> <span>string</span>       | State for the address            |
| zip <br> <span>string</span>         | Zip Code for the address         |
| country <br> <span>string</span>     | Country for the address          |
| phone <br> <span>string</span>       | Phone number for the address     |

### Factory Address

```json
# Standard Object - Used in a resource collection
{
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
```

Standard Attributes

| Attribute                            | Description                      |
| ------------------------------------ | -------------------------------- |
| id <br> <span>integer</span>         | Unique identifier for the object |
| description <br> <span>string</span> | Brief description of address     |
| street1 <br> <span>string</span>     | First street line of address     |
| street2 <br> <span>string</span>     | Second street line of address    |
| street3 <br> <span>string</span>     | Third street line of address     |
| city <br> <span>string</span>        | City for the address             |
| state <br> <span>string</span>       | State for the address            |
| zip <br> <span>string</span>         | Zip Code for the address         |
| country <br> <span>string</span>     | Country for the address          |
| phone <br> <span>string</span>       | Phone number for the address     |

### Dealer

```json
# Standard Object - Used in a resource collection
{
    "id": 1106,
    "name": "Studio Garments",
    "first_name": "Studio",
    "last_name": "Garments",
    "company_name": null,
    "email": "jwiggins@idpbp.com",
    "phone": "6017132628",
    "country": "USA"
}
```

Standard Attributes

| Attribute                             | Description                             |
| ------------------------------------- | --------------------------------------- |
| id <br> <span>integer</span>          | Unique identifier for the object        |
| name <br> <span>string</span>         | Combined string for first and last name |
| first_name <br> <span>string</span>   | First name of the dealer                |
| last_name <br> <span>string</span>    | Last name of the dealer                 |
| company_name <br> <span>string</span> | Name of the dealer's company            |
| email <br> <span>string</span>        | Email address of the dealer             |
| phone <br> <span>string</span>        | Phone number of the dealer              |
| country <br> <span>string</span>      | Country where the dealer is             |

### Customer

```json
# Standard Object - Used in a resource collection
{
    "id": 87285,
    "created_at": "2016-05-29T15:08:38.000Z",
    "name": "Mr Mannequin",
    "first_name": "Mr",
    "last_name": "Mannequin",
    "email": null
}
```

Standard Attributes

| Attribute                             | Description                             |
| ------------------------------------- | --------------------------------------- |
| id <br> <span>integer</span>          | Unique identifier for the object        |
| created_at <br> <span>datetime</span> | *Description TBD*                       |
| name <br> <span>string</span>         | Combined string for first and last name |
| first_name <br> <span>string</span>   | First name of the customer              |
| last_name <br> <span>string</span>    | Last name of the customer               |
| email <br> <span>string</span>        | Email address of the customer           |

### Garment

```json
# Standard Object - Used in a resource collection
{
    "id": 892902,
    "title": "ID-892902",
    "order_id": 407781,
    "copied_garment_id": null,
    "price": "66.0",
    "option_cost": "0.0",
    "garment_type": "CSHT",
    "created_at": "2018-08-17T09:50:45.000Z",
    "updated_at": "2018-08-29T03:52:13.000Z",
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
| price <br> <span>decimal</span>             | Wholesale cost of the garment                                                                                    |
| option_cost <br> <span>decimal</span>       | Dollar cost of the premium options used in this garment                                                          |
| garment_type <br> <span>string</span>       | Type of garment. [Click here](#garment-types) for more info                                                      |
| created_at <br> <span>datetime</span>       | When the garment was first created (but not ordered)                                                             |
| updated_at <br> <span>datetime</span>       | When the garment was last modified                                                                               |
| order_status <br> <span>subresource</span>  | Current status of the order. [Click here](#order-statuses) for more info                                         |
| delay_status <br> <span>subresource</span>  | If garment is delayed, this will return why. [Click here](#delay-statuses) for more info                         |
| dealer_order <br> <span>subresource</span>  | The full order placed by a single customer. Includes this garment and can include more garments.                 |

```json
# Extended Object
{
    "id": 892902,
    "title": "ID-892902",
    "order_id": 407781,
    "copied_garment_id": null,
    "price": "66.0",
    "option_cost": "0.0",
    "garment_type": "CSHT",
    "created_at": "2018-08-17T09:50:45.000Z",
    "updated_at": "2018-08-29T03:52:13.000Z",
    "prefix": "ID",
    "index": "2/2",
    "last_status_change_date": "2018-09-14T14:20:40.000Z",
    "last_delay_change_date": null,
    "order_status": ...,
    "delay_status": ...,
    "dealer_order": ...,
    "manufacturer": ...,
    "fabric": ...
}
```

Extended Attributes

| Attribute               | Type        | Description                                                                                                 |
| ----------------------- | ----------- | ----------------------------------------------------------------------------------------------------------- |
| prefix                  | string      | First part of the title. This indicates where the order was made or where the factory will send the garment |
| index                   | string      | Sequence number (1/7, 2/7, 3/7 ...) for each garment in an order. Each item has a different index           |
| last_status_change_date | datetime    | When did the order status last change to a new state                                                        |
| last_delay_change_date  | datetime    | When did the delay status last change to a new state                                                        |
| manufacturer            | subresource | The factory who made the garment                                                                            |
| fabric                  | subresource | Information about the primary fabric used for the garment                                                   |

### Order Status

```json
# Standard Object - Used in a resource collection
{
    "code": "SHIPCUST",
    "name": "Delivery",
    "description": "Delivery"
}
```

Standard Attributes - [see here](#order-statuses) for details

| Attribute                            | Description                   |
| ------------------------------------ | ----------------------------- |
| code <br> <span>string</span>        | Trinity code for order status |
| name <br> <span>string</span>        | The name of the order status  |
| description <br> <span>string</span> | Description of order status   |

### Delay Status

```json
# Standard Object - Used in a resource collection
{
    "code": "OK",
    "description": "Not Delayed"
}
```

Standard Attributes - [see here](#delay-statuses) for details

| Attribute                            | Description                   |
| ------------------------------------ | ----------------------------- |
| code <br> <span>string</span>        | Trinity code for delay status |
| description <br> <span>string</span> | Description of delay status   |

### Manufacturer

```json
# Standard Object - Used in a resource collection
{
    "id": 2,
    "address_id": 1943,
    "name": "iD Shirts",
    "email": "info@trinity-apparel.com"
}
```

Standard Attributes

| Attribute                      | Description                       |
| ------------------------------ | --------------------------------- |
| id <br> <span>integer</span>   | Unique identifier for the object  |
| name <br> <span>string</span>  | Name of the manufacturer          |
| email <br> <span>string</span> | Email address of the manufacturer |

### Garment Options

```json
# Standard Object - Used in a resource collection
{
    "updated_at": "2019-02-12T16:36:59.000Z",
    "text": null,
    "option": ...,
    "option_value": ...
}
```

Standard Attributes

| Attribute                                  | Description                                                                            |
| ------------------------------------------ | -------------------------------------------------------------------------------------- |
| updated_at <br> <span>datetime</span>      | The last time the garment option was updated.                                          |
| text <br> <span>string</span>              | If the option has a text value (E.g., monogram, label, etc), it will be returned here. |
| option <br> <span>subresource</span>       | Detailed object for the option.                                                        |
| option_value <br> <span>subresource</span> | Detailed object for the option value.                                                  |

### Option

```json
# Standard Object - Used in a resource collection
{
    "id": 1,
    "garment_type": 545,
    "tailoring_grade": 895,
    "order_type": 3,
    "name": "garment_label",
    "description": "Garment Label",
    "gerber_option": false,
    "option_operator": "A1",
    "option_group_id": 27,
    "material_type_id": 0,
    "option_location": "interior",
    "option_control_type": "select",
    "popup_text": null,
    "parent_option_id": null,
    "display_order": 5,
    "active": true
}
```

Standard Attributes

| Attribute                                    | Description                       |
| -------------------------------------------- | --------------------------------- |
| id <br> <span>integer</span>                 | Unique identifier for the object. |
| garment_type <br> <span>integer</span>       | *Description TBD*                 |
| tailoring_grade <br> <span>integer</span>    | *Description TBD*                 |
| order_type <br> <span>integer</span>         | *Description TBD*                 |
| name <br> <span>string</span>                | *Description TBD*                 |
| description <br> <span>string</span>         | *Description TBD*                 |
| gerber_option <br> <span>boolean</span>      | *Description TBD*                 |
| option_operator <br> <span>string</span>     | *Description TBD*                 |
| option_group_id <br> <span>integer</span>    | *Description TBD*                 |
| material_type_id <br> <span>integer</span>   | *Description TBD*                 |
| option_locator <br> <span>string</span>      | *Description TBD*                 |
| option_control_type <br> <span>string</span> | *Description TBD*                 |
| popup_text <br> <span>string</span>          | *Description TBD*                 |
| parent_option_id <br> <span>integer</span>   | *Description TBD*                 |
| display_order <br> <span>integer</span>      | *Description TBD*                 |
| active <br> <span>boolean</span>             | *Description TBD*                 |

### Option Value

```json
# Standard Object - Used in a resource collection
{
    "id": 4,
    "garment_type": 545,
    "tailoring_grade": 895,
    "order_type": 3,
    "option_value": "no_label",
    "gerber_optval": false,
    "rc_price": "0.0",
    "premium_id": 1,
    "default_value": true,
    "copyable": true,
    "display_order": 2,
    "active": true,
    "description": "No Label"
}
```

Standard Attributes

| Attribute                                 | Description                       |
| ----------------------------------------- | --------------------------------- |
| id <br> <span>integer</span>              | Unique identifier for the object. |
| garment_type <br> <span>integer</span>    | *Description TBD*                 |
| tailoring_grade <br> <span>integer</span> | *Description TBD*                 |
| order_type <br> <span>integer</span>      | *Description TBD*                 |
| option_value <br> <span>string</span>     | *Description TBD*                 |
| gerber_optval <br> <span>boolean</span>   | *Description TBD*                 |
| rc_price <br> <span>string</span>         | *Description TBD*                 |
| premium_id <br> <span>integer</span>      | *Description TBD*                 |
| default_value <br> <span>boolean</span>   | *Description TBD*                 |
| copyable <br> <span>boolean</span>        | *Description TBD*                 |
| display_order <br> <span>integer</span>   | *Description TBD*                 |
| active <br> <span>boolean</span>          | *Description TBD*                 |
| description <br> <span>string</span>      | *Description TBD*                 |

### Garment Measurements

```json
# Standard Object - Used in a resource collection
{
    "updated_at": "2018-08-10T21:29:27.000Z",
    "text": "0.000",
    "measurement": ...,
    "measurement_value": ...
}
```

Standard Attributes

| Attribute                                      | Description                                   |
| ---------------------------------------------- | --------------------------------------------- |
| updated_at <br> <span>datetime</span>          | The last time the garment option was updated. |
| text <br> <span>string</span>                  | *Description TBD*                             |
| measurement <br> <span>subresource</span>      | Detailed object for the measurement.          |
| meaurement_value <br> <span>subresource</span> | Detailed object for measurement value.        |

### Measurement

```json
# Standard Object - Used in a resource collection
{
    "id": 7,
    "name": "perkins_incline",
    "description": "Incline Reading",
    "description_zh_cn": "正常",
    "garment_type": 239,
    "tailoring_grade": 511,
    "isdropdown": 0,
    "display_order": 5
}
```

Standard Attributes

| Attribute                                  | Description                       |
| ------------------------------------------ | --------------------------------- |
| id <br> <span>integer</span>               | Unique identifier for the object. |
| name <br> <span>string</span>              | *Description TBD*                 |
| description <br> <span>string</span>       | *Description TBD*                 |
| description_zh_cn <br> <span>string</span> | *Description TBD*                 |
| garment_type <br> <span>integer</span>     | *Description TBD*                 |
| tailoring_grade <br> <span>integer</span>  | *Description TBD*                 |
| isdropdown <br> <span>boolean</span>       | *Description TBD*                 |
| display_order <br> <span>integer</span>    | *Description TBD*                 |

### Measurement Value

```json
# Standard Object - Used in a resource collection
{
    "id": 16,
    "value": "0.000",
    "description": "",
    "description_zh_cn": "",
    "default_value": 1,
    "display_order": 1,
    "active": 1
}
```

Standard Attributes

| Attribute                                  | Description                       |
| ------------------------------------------ | --------------------------------- |
| id <br> <span>integer</span>               | Unique identifier for the object. |
| value <br> <span>string</span>             | *Description TBD*                 |
| description <br> <span>string</span>       | *Description TBD*                 |
| description_zh_cn <br> <span>string</span> | *Description TBD*                 |
| default_value <br> <span>integer</span>    | *Description TBD*                 |
| display_order <br> <span>integer</span>    | *Description TBD*                 |
| active <br> <span>boolean</span>           | *Description TBD*                 |

## Get All Orders (DOs)

```shell
curl "https://api.trinity-apparel.com/v1/orders"
  -H "Authorization Bearer: swaledale"
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

| Parameter | Default | Description                                                                                                       |
| --------- | ------- | ----------------------------------------------------------------------------------------------------------------- |
| is_active | true    | If set to true, the result will only include active fabrics                                                       |
| extended  | false   | If set to true, the API call returns extended objects which include a complete set of attributes and subresources |

### Other

- Permissions: All
- Pagination: Yes

## Get a Specific Order

```shell
curl "https://api.trinity-apparel.com/v1/orders/399780"
  -H "Authorization Bearer: swaledale"
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
            "price": "274.0",
            "option_cost": "65.0",
            "garment_type": "CSC",
            "created_at": "2018-06-29T09:44:15.000Z",
            "updated_at": "2018-08-03T04:01:21.000Z"
        },
        {
            "id": 872909,
            "title": "ID-872909",
            "order_id": 399780,
            "copied_garment_id": 872898,
            "price": "274.0",
            "option_cost": "65.0",
            "garment_type": "CSC",
            "created_at": "2018-06-29T10:02:12.000Z",
            "updated_at": "2018-07-27T03:35:22.000Z"
        },
        {
            "id": 872918,
            "title": "ID-872918",
            "order_id": 399780,
            "copied_garment_id": 872909,
            "price": "274.0",
            "option_cost": "65.0",
            "garment_type": "CSC",
            "created_at": "2018-06-29T10:20:23.000Z",
            "updated_at": "2018-07-25T04:05:58.000Z"
        },
        {
            "id": 872919,
            "title": "ID-872919",
            "order_id": 399780,
            "copied_garment_id": 872898,
            "price": "274.0",
            "option_cost": "65.0",
            "garment_type": "CSC",
            "created_at": "2018-06-29T10:26:58.000Z",
            "updated_at": "2018-07-23T03:51:47.000Z"
        },
        {
            "id": 872920,
            "title": "ID-872920",
            "order_id": 399780,
            "copied_garment_id": 872918,
            "price": "460.0",
            "option_cost": "60.0",
            "garment_type": "CSC",
            "created_at": "2018-06-29T10:30:15.000Z",
            "updated_at": "2018-07-26T03:38:01.000Z"
        },
        {
            "id": 872932,
            "title": "ID-872932",
            "order_id": 399780,
            "copied_garment_id": 872920,
            "price": "274.0",
            "option_cost": "65.0",
            "garment_type": "CSC",
            "created_at": "2018-06-29T10:45:08.000Z",
            "updated_at": "2018-07-23T03:51:40.000Z"
        },
        {
            "id": 872933,
            "title": "ID-872933",
            "order_id": 399780,
            "copied_garment_id": 872932,
            "price": "274.0",
            "option_cost": "65.0",
            "garment_type": "CSC",
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

| Parameter | Default | Description                           |
| --------- | ------- | ------------------------------------- |
| id        | N/A     | The specific order id you want to see |

### Other

- Permissions: All
- Pagination: N/A

## Get All Garments

```shell
curl "https://api.trinity-apparel.com/v1/garments"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 892902,
        "title": "ID-892902",
        "order_id": 407781,
        "copied_garment_id": null,
        "price": "66.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-08-17T09:50:45.000Z",
        "updated_at": "2018-08-29T03:52:13.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 407781,
            "title": "DO-407781",
            "custom_order_number": null,
            "garment_count": 2,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "416.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "416.0",
            "deposit_percentage": 50,
            "current_balance": "416.0",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-08-17T09:54:23.000Z",
            "created_at": "2018-08-09T10:41:20.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 892263,
        "title": "ID-892263",
        "order_id": 408973,
        "copied_garment_id": 856350,
        "price": "90.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-08-15T16:43:09.000Z",
        "updated_at": "2018-08-15T16:43:09.000Z",
        "order_status": {
            "code": "INCOMPLETE",
            "name": "Incomplete",
            "description": "Incomplete"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 408973,
            "title": "DO-408973",
            "custom_order_number": "",
            "garment_count": 0,
            "ship_type": "Ground",
            "ship_cost": "0.0",
            "subtotal": "0.0",
            "dealer_discount": "0.0",
            "total_discount": null,
            "tax": "0.0",
            "grand_total": "0.0",
            "deposit_percentage": 100,
            "current_balance": "0.0",
            "measurement_units": "uscust",
            "payment_status": "incomplete",
            "ordered_at": null,
            "created_at": "2018-08-15T16:41:14.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 895396,
        "title": "ID-895396",
        "order_id": 410469,
        "copied_garment_id": 888670,
        "price": "66.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-08-23T16:34:03.000Z",
        "updated_at": "2018-09-06T02:46:09.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 410469,
            "title": "DO-410469",
            "custom_order_number": null,
            "garment_count": 3,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "504.5",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "504.5",
            "deposit_percentage": 50,
            "current_balance": "504.5",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-08-23T16:40:53.000Z",
            "created_at": "2018-08-23T16:20:26.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 895401,
        "title": "ID-895401",
        "order_id": 410469,
        "copied_garment_id": 895396,
        "price": "54.0",
        "option_cost": "4.5",
        "garment_type": "CSHT",
        "created_at": "2018-08-23T16:39:55.000Z",
        "updated_at": "2018-09-06T02:46:02.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 410469,
            "title": "DO-410469",
            "custom_order_number": null,
            "garment_count": 3,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "504.5",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "504.5",
            "deposit_percentage": 50,
            "current_balance": "504.5",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-08-23T16:40:53.000Z",
            "created_at": "2018-08-23T16:20:26.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 896118,
        "title": "ID-896118",
        "order_id": 410677,
        "copied_garment_id": null,
        "price": "85.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-08-27T09:58:53.000Z",
        "updated_at": "2018-09-06T02:45:58.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 410677,
            "title": "DO-410677",
            "custom_order_number": null,
            "garment_count": 2,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "745.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "745.0",
            "deposit_percentage": 50,
            "current_balance": "745.0",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-08-27T10:16:22.000Z",
            "created_at": "2018-08-24T16:17:43.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 897997,
        "title": "ID-897997",
        "order_id": 411784,
        "copied_garment_id": null,
        "price": "75.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-08-30T14:29:48.000Z",
        "updated_at": "2018-09-11T03:38:42.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 411784,
            "title": "DO-411784",
            "custom_order_number": null,
            "garment_count": 1,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "75.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "75.0",
            "deposit_percentage": 50,
            "current_balance": "75.0",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-08-30T14:39:11.000Z",
            "created_at": "2018-08-30T14:22:12.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 899861,
        "title": "ID-899861",
        "order_id": 412640,
        "copied_garment_id": null,
        "price": "66.0",
        "option_cost": "10.0",
        "garment_type": "CSHT",
        "created_at": "2018-09-05T11:23:57.000Z",
        "updated_at": "2018-09-10T02:21:23.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 412640,
            "title": "DO-412640",
            "custom_order_number": "photo shoot samples",
            "garment_count": 2,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "676.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "676.0",
            "deposit_percentage": 50,
            "current_balance": "676.0",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-09-05T15:45:42.000Z",
            "created_at": "2018-09-05T11:04:38.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 905041,
        "title": "ID-905041",
        "order_id": 412892,
        "copied_garment_id": null,
        "price": "66.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-09-17T09:43:02.000Z",
        "updated_at": null,
        "order_status": {
            "code": "INCOMPLETE",
            "name": "Incomplete",
            "description": "Incomplete"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 412892,
            "title": "DO-412892",
            "custom_order_number": "",
            "garment_count": 0,
            "ship_type": "Ground",
            "ship_cost": "0.0",
            "subtotal": "0.0",
            "dealer_discount": "0.0",
            "total_discount": null,
            "tax": "0.0",
            "grand_total": "0.0",
            "deposit_percentage": 100,
            "current_balance": "0.0",
            "measurement_units": "uscust",
            "payment_status": "incomplete",
            "ordered_at": null,
            "created_at": "2018-09-06T10:36:15.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 902379,
        "title": "ID-902379",
        "order_id": 413845,
        "copied_garment_id": null,
        "price": "71.0",
        "option_cost": "4.5",
        "garment_type": "CSHT",
        "created_at": "2018-09-11T14:36:26.000Z",
        "updated_at": "2018-09-18T03:10:01.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 413845,
            "title": "DO-413845",
            "custom_order_number": null,
            "garment_count": 3,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "710.5",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "710.5",
            "deposit_percentage": 50,
            "current_balance": "710.5",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-09-11T14:39:53.000Z",
            "created_at": "2018-09-11T14:21:09.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 904299,
        "title": "ID-904299",
        "order_id": 414761,
        "copied_garment_id": 892902,
        "price": "71.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-09-14T14:22:11.000Z",
        "updated_at": "2018-09-25T03:49:35.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 414761,
            "title": "DO-414761",
            "custom_order_number": null,
            "garment_count": 3,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "198.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "198.0",
            "deposit_percentage": 50,
            "current_balance": "198.0",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-09-14T14:34:48.000Z",
            "created_at": "2018-09-14T14:21:04.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 904303,
        "title": "ID-904303",
        "order_id": 414761,
        "copied_garment_id": 892902,
        "price": "66.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-09-14T14:25:48.000Z",
        "updated_at": "2018-09-25T03:50:02.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 414761,
            "title": "DO-414761",
            "custom_order_number": null,
            "garment_count": 3,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "198.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "198.0",
            "deposit_percentage": 50,
            "current_balance": "198.0",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-09-14T14:34:48.000Z",
            "created_at": "2018-09-14T14:21:04.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 904305,
        "title": "ID-904305",
        "order_id": 414761,
        "copied_garment_id": 904303,
        "price": "61.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-09-14T14:29:07.000Z",
        "updated_at": "2018-09-25T03:49:30.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 414761,
            "title": "DO-414761",
            "custom_order_number": null,
            "garment_count": 3,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "198.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "198.0",
            "deposit_percentage": 50,
            "current_balance": "198.0",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-09-14T14:34:48.000Z",
            "created_at": "2018-09-14T14:21:04.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 904374,
        "title": "ID-904374",
        "order_id": 414783,
        "copied_garment_id": 895396,
        "price": "66.0",
        "option_cost": "4.5",
        "garment_type": "CSHT",
        "created_at": "2018-09-14T15:58:21.000Z",
        "updated_at": "2018-09-25T03:52:14.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 414783,
            "title": "DO-414783",
            "custom_order_number": null,
            "garment_count": 2,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "146.5",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "146.5",
            "deposit_percentage": 50,
            "current_balance": "146.5",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-09-14T16:03:13.000Z",
            "created_at": "2018-09-14T15:57:53.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 904376,
        "title": "ID-904376",
        "order_id": 414783,
        "copied_garment_id": 895396,
        "price": "76.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-09-14T16:00:52.000Z",
        "updated_at": "2018-09-27T03:31:31.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 414783,
            "title": "DO-414783",
            "custom_order_number": null,
            "garment_count": 2,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "146.5",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "146.5",
            "deposit_percentage": 50,
            "current_balance": "146.5",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-09-14T16:03:13.000Z",
            "created_at": "2018-09-14T15:57:53.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 910833,
        "title": "ID-910833",
        "order_id": 417697,
        "copied_garment_id": null,
        "price": "76.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-09-29T23:10:18.000Z",
        "updated_at": null,
        "order_status": {
            "code": "INCOMPLETE",
            "name": "Incomplete",
            "description": "Incomplete"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 417697,
            "title": "DO-417697",
            "custom_order_number": null,
            "garment_count": 0,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "0.0",
            "dealer_discount": "0.0",
            "total_discount": null,
            "tax": "0.0",
            "grand_total": "0.0",
            "deposit_percentage": 50,
            "current_balance": "0.0",
            "measurement_units": "uscust",
            "payment_status": "incomplete",
            "ordered_at": null,
            "created_at": "2018-09-29T22:59:50.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 912228,
        "title": "ID-912228",
        "order_id": 418267,
        "copied_garment_id": 856350,
        "price": "90.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-10-02T16:38:48.000Z",
        "updated_at": "2018-10-23T03:38:52.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 418267,
            "title": "DO-418267",
            "custom_order_number": null,
            "garment_count": 3,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "745.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "745.0",
            "deposit_percentage": 50,
            "current_balance": "745.0",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-10-05T15:33:18.000Z",
            "created_at": "2018-10-02T16:17:51.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 912231,
        "title": "ID-912231",
        "order_id": 418267,
        "copied_garment_id": 856347,
        "price": "75.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-10-02T16:40:35.000Z",
        "updated_at": "2018-10-18T03:15:45.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 418267,
            "title": "DO-418267",
            "custom_order_number": null,
            "garment_count": 3,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "745.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "745.0",
            "deposit_percentage": 50,
            "current_balance": "745.0",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-10-05T15:33:18.000Z",
            "created_at": "2018-10-02T16:17:51.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 913375,
        "title": "ID-913375",
        "order_id": 418457,
        "copied_garment_id": null,
        "price": "66.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-10-04T15:30:18.000Z",
        "updated_at": null,
        "order_status": {
            "code": "INCOMPLETE",
            "name": "Incomplete",
            "description": "Incomplete"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 418457,
            "title": "DO-418457",
            "custom_order_number": "",
            "garment_count": 0,
            "ship_type": "Ground",
            "ship_cost": "0.0",
            "subtotal": "0.0",
            "dealer_discount": "0.0",
            "total_discount": null,
            "tax": "0.0",
            "grand_total": "0.0",
            "deposit_percentage": 100,
            "current_balance": "0.0",
            "measurement_units": "uscust",
            "payment_status": "incomplete",
            "ordered_at": null,
            "created_at": "2018-10-03T13:26:13.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 913251,
        "title": "ID-913251",
        "order_id": 418746,
        "copied_garment_id": 878112,
        "price": "66.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-10-04T13:52:18.000Z",
        "updated_at": "2018-10-15T03:36:23.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 418746,
            "title": "DO-418746",
            "custom_order_number": null,
            "garment_count": 6,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "644.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "644.0",
            "deposit_percentage": 50,
            "current_balance": "644.0",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-10-04T13:59:15.000Z",
            "created_at": "2018-10-04T13:50:37.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 913254,
        "title": "ID-913254",
        "order_id": 418746,
        "copied_garment_id": 913251,
        "price": "66.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-10-04T13:52:55.000Z",
        "updated_at": "2018-10-15T03:32:50.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 418746,
            "title": "DO-418746",
            "custom_order_number": null,
            "garment_count": 6,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "644.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "644.0",
            "deposit_percentage": 50,
            "current_balance": "644.0",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-10-04T13:59:15.000Z",
            "created_at": "2018-10-04T13:50:37.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 913255,
        "title": "ID-913255",
        "order_id": 418746,
        "copied_garment_id": 913254,
        "price": "66.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-10-04T13:53:40.000Z",
        "updated_at": "2018-10-15T03:32:49.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 418746,
            "title": "DO-418746",
            "custom_order_number": null,
            "garment_count": 6,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "644.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "644.0",
            "deposit_percentage": 50,
            "current_balance": "644.0",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-10-04T13:59:15.000Z",
            "created_at": "2018-10-04T13:50:37.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 913263,
        "title": "ID-913263",
        "order_id": 418746,
        "copied_garment_id": 913255,
        "price": "66.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-10-04T13:56:50.000Z",
        "updated_at": "2018-10-15T03:32:48.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 418746,
            "title": "DO-418746",
            "custom_order_number": null,
            "garment_count": 6,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "644.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "644.0",
            "deposit_percentage": 50,
            "current_balance": "644.0",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-10-04T13:59:15.000Z",
            "created_at": "2018-10-04T13:50:37.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 915901,
        "title": "ID-915901",
        "order_id": 420034,
        "copied_garment_id": null,
        "price": "109.0",
        "option_cost": "0.0",
        "garment_type": "CSHT",
        "created_at": "2018-10-10T14:48:27.000Z",
        "updated_at": "2018-10-26T02:59:40.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 420034,
            "title": "DO-420034",
            "custom_order_number": null,
            "garment_count": 1,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "109.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "109.0",
            "deposit_percentage": 50,
            "current_balance": "109.0",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-10-10T15:06:28.000Z",
            "created_at": "2018-10-10T14:46:24.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 918812,
        "title": "ID-918812",
        "order_id": 421405,
        "copied_garment_id": null,
        "price": "55.0",
        "option_cost": "10.0",
        "garment_type": "CSHT",
        "created_at": "2018-10-17T12:18:47.000Z",
        "updated_at": "2018-10-31T02:50:32.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 421405,
            "title": "DO-421405",
            "custom_order_number": null,
            "garment_count": 1,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "65.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "65.0",
            "deposit_percentage": 50,
            "current_balance": "65.0",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-10-17T12:26:45.000Z",
            "created_at": "2018-10-17T12:17:56.000Z",
            "invoiced_at": null
        }
    },
    {
        "id": 919662,
        "title": "ID-919662",
        "order_id": 421718,
        "copied_garment_id": null,
        "price": "109.0",
        "option_cost": "4.5",
        "garment_type": "CSHT",
        "created_at": "2018-10-18T15:23:42.000Z",
        "updated_at": "2018-10-29T03:09:48.000Z",
        "order_status": {
            "code": "SHIPCUST",
            "name": "Delivery",
            "description": "Delivery"
        },
        "delay_status": {
            "code": "OK",
            "description": "Not Delayed"
        },
        "dealer_order": {
            "id": 421718,
            "title": "DO-421718",
            "custom_order_number": null,
            "garment_count": 2,
            "ship_type": "In-Store Pick-Up",
            "ship_cost": "0.0",
            "subtotal": "227.0",
            "dealer_discount": "0.0",
            "total_discount": "0.0",
            "tax": "0.0",
            "grand_total": "227.0",
            "deposit_percentage": 50,
            "current_balance": "218.0",
            "measurement_units": "uscust",
            "payment_status": "offline",
            "ordered_at": "2018-10-18T15:35:38.000Z",
            "created_at": "2018-10-18T12:49:16.000Z",
            "invoiced_at": null
        }
    }
]
```

Returns an array of garments.  Each garment will have pricing information and order status information.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/garments`

### Query Parameters

| Parameter         | Default | Description                                                                                                       |
| ----------------- | ------- | ----------------------------------------------------------------------------------------------------------------- |
| order_id          | N/A     | Show garments that are part of a specific dealer order                                                            |
| order_status_code | N/A     | Show garments that are in a specific order status                                                                 |
| delay_status_code | N/A     | Show garments that are in a specific delay status                                                                 |
| extended          | false   | If set to true, the API call returns extended objects which include a complete set of attributes and subresources |

### Other

- Permissions: All
- Pagination: Yes

## Get a Specific Garment

```shell
curl "https://api.trinity-apparel.com/v1/garments/399780"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
    "id": 892902,
    "title": "ID-892902",
    "order_id": 407781,
    "copied_garment_id": null,
    "price": "66.0",
    "option_cost": "0.0",
    "garment_type": "CSHT",
    "created_at": "2018-08-17T09:50:45.000Z",
    "updated_at": "2018-08-29T03:52:13.000Z",
    "prefix": "ID",
    "index": "2/2",
    "last_status_change_date": "2018-09-14T14:20:40.000Z",
    "last_delay_change_date": null,
    "order_status": {
        "code": "SHIPCUST",
        "name": "Delivery",
        "description": "Delivery"
    },
    "delay_status": {
        "code": "OK",
        "description": "Not Delayed"
    },
    "dealer_order": {
        "id": 407781,
        "title": "DO-407781",
        "custom_order_number": null,
        "garment_count": 2,
        "ship_type": "In-Store Pick-Up",
        "ship_cost": "0.0",
        "subtotal": "416.0",
        "dealer_discount": "0.0",
        "total_discount": "0.0",
        "tax": "0.0",
        "grand_total": "416.0",
        "deposit_percentage": 50,
        "current_balance": "416.0",
        "measurement_units": "uscust",
        "payment_status": "offline",
        "ordered_at": "2018-08-17T09:54:23.000Z",
        "created_at": "2018-08-09T10:41:20.000Z",
        "invoiced_at": null
    },
    "manufacturer": {
        "id": 2,
        "address_id": 1943,
        "name": "iD Shirts",
        "email": "info@trinity-apparel.com"
    },
    "fabric": {
        "id": 27284,
        "active": true,
        "in_stock": 1,
        "restock_date": null,
        "description": "White Fine Twill",
        "supplier_fabric_number": "#12 White",
        "trinity_fabric_number": "N3-3127284",
        "url": "https://s7d4.scene7.com/is/image/trinityapparel/N3-3127284",
        "swatch_url": "https://s7d4.scene7.com/ir/render/trinityapparelrender/SwatchWorkflo?obj=Swatch/Fabric&src=N3-3127284&res=300",
        "inventory_status": "In Stock"
    }
}
```

Returns details on a specific garment.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/garments/:id`

### Query Parameters

| Parameter | Default | Description                             |
| --------- | ------- | --------------------------------------- |
| id        | N/A     | The specific garment id you want to see |

### Other

- Permissions: All
- Pagination: N/A

## Get All Garment Options

```shell
curl "https://api.trinity-apparel.com/v1/garments/966400/options"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "updated_at": "2019-02-12T16:36:59.000Z",
        "text": null,
        "option": {
            "id": 1,
            "garment_type": 545,
            "tailoring_grade": 895,
            "order_type": 3,
            "name": "garment_label",
            "description": "Garment Label",
            "gerber_option": false,
            "option_operator": "A1",
            "option_group_id": 27,
            "material_type_id": 0,
            "option_location": "interior",
            "option_control_type": "select",
            "popup_text": null,
            "parent_option_id": null,
            "display_order": 5,
            "active": true
        },
        "option_value": {
            "id": 4,
            "garment_type": 545,
            "tailoring_grade": 895,
            "order_type": 3,
            "option_value": "no_label",
            "gerber_optval": false,
            "rc_price": "0.0",
            "premium_id": 1,
            "default_value": true,
            "copyable": true,
            "display_order": 2,
            "active": true,
            "description": "No Label"
        }
    },
    {
        "updated_at": "2019-02-12T16:36:59.000Z",
        "text": null,
        "option": {
            "id": 2,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "name": "vent_style",
            "description": "Vent Style",
            "gerber_option": true,
            "option_operator": "B1",
            "option_group_id": 30,
            "material_type_id": 0,
            "option_location": "exterior",
            "option_control_type": "select",
            "popup_text": null,
            "parent_option_id": null,
            "display_order": 1,
            "active": true
        },
        "option_value": {
            "id": 7,
            "garment_type": 1,
            "tailoring_grade": 895,
            "order_type": 3,
            "option_value": "side_vent",
            "gerber_optval": true,
            "rc_price": "0.0",
            "premium_id": 1,
            "default_value": true,
            "copyable": true,
            "display_order": 6,
            "active": true,
            "description": "Sides (9 1/2\") - Standard"
        }
    },
    {
        "updated_at": "2019-02-12T16:38:47.000Z",
        "text": null,
        "option": {
            "id": 3,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "name": "shoulder_style",
            "description": "Shoulder Style",
            "gerber_option": true,
            "option_operator": "B5",
            "option_group_id": 29,
            "material_type_id": 0,
            "option_location": "exterior",
            "option_control_type": "select",
            "popup_text": null,
            "parent_option_id": null,
            "display_order": 1,
            "active": true
        },
        "option_value": {
            "id": 656,
            "garment_type": 33,
            "tailoring_grade": 383,
            "order_type": 3,
            "option_value": "ultra_soft",
            "gerber_optval": true,
            "rc_price": "0.0",
            "premium_id": 1,
            "default_value": false,
            "copyable": true,
            "display_order": 0,
            "active": true,
            "description": "Ultra Soft"
        }
    },
    {
        "updated_at": "2019-02-12T16:36:59.000Z",
        "text": null,
        "option": {
            "id": 4,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "name": "exterior_breast_pocket",
            "description": "Exterior Breast Pocket",
            "gerber_option": true,
            "option_operator": "A1",
            "option_group_id": 2,
            "material_type_id": 0,
            "option_location": "exterior",
            "option_control_type": "select",
            "popup_text": null,
            "parent_option_id": null,
            "display_order": 1,
            "active": true
        },
        "option_value": {
            "id": 730,
            "garment_type": 1,
            "tailoring_grade": 383,
            "order_type": 3,
            "option_value": "welt_curved_square",
            "gerber_optval": true,
            "rc_price": "0.0",
            "premium_id": 1,
            "default_value": false,
            "copyable": true,
            "display_order": 3,
            "active": true,
            "description": "Welt (Curved, Square Edges)"
        }
    },
    {
        "updated_at": "2019-02-12T16:39:03.000Z",
        "text": null,
        "option": {
            "id": 5,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "name": "ticket_pocket",
            "description": "Ticket Pocket",
            "gerber_option": true,
            "option_operator": "A1",
            "option_group_id": 2,
            "material_type_id": 0,
            "option_location": "exterior",
            "option_control_type": "select",
            "popup_text": null,
            "parent_option_id": null,
            "display_order": 5,
            "active": true
        },
        "option_value": {
            "id": 771,
            "garment_type": 33,
            "tailoring_grade": 383,
            "order_type": 3,
            "option_value": "patch",
            "gerber_optval": true,
            "rc_price": "0.0",
            "premium_id": 1,
            "default_value": false,
            "copyable": true,
            "display_order": 15,
            "active": true,
            "description": "Patch"
        }
    },
    {
        "updated_at": "2019-02-12T16:36:59.000Z",
        "text": null,
        "option": {
            "id": 6,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "name": "exterior_lower_pockets",
            "description": "Exterior Lower Pockets",
            "gerber_option": true,
            "option_operator": "A1",
            "option_group_id": 2,
            "material_type_id": 0,
            "option_location": "exterior",
            "option_control_type": "select",
            "popup_text": "Microsuede Pocket Jetting is only available on Double Besom pockets",
            "parent_option_id": null,
            "display_order": 9,
            "active": true
        },
        "option_value": {
            "id": 18,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "option_value": "patch",
            "gerber_optval": true,
            "rc_price": "0.0",
            "premium_id": 1,
            "default_value": false,
            "copyable": true,
            "display_order": 15,
            "active": true,
            "description": "Patch"
        }
    },
    {
        "updated_at": "2019-02-12T16:36:59.000Z",
        "text": null,
        "option": {
            "id": 7,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "name": "interior_breast_pocket_l",
            "description": "Interior Breast Pocket (L)",
            "gerber_option": true,
            "option_operator": "A1",
            "option_group_id": 2,
            "material_type_id": 0,
            "option_location": "interior",
            "option_control_type": "select",
            "popup_text": "Cellphone Pocket: Left and Pen/Pencil Pocket: Left cannot be ordered with Interior Breast Pocket (L): Double Besom Button-Through\nIf Interior Breast Pocket L: Patch Pockets are chosen, Interior Shape: Parallel is required\nShell Fabric Pocket Fasteners are only available on Interior Breast Pockets with Loop, Flap, or Tab",
            "parent_option_id": null,
            "display_order": 1,
            "active": true
        },
        "option_value": {
            "id": 1299,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "option_value": "double_besom",
            "gerber_optval": true,
            "rc_price": "0.0",
            "premium_id": 1,
            "default_value": true,
            "copyable": true,
            "display_order": 2,
            "active": true,
            "description": "Double Besom"
        }
    },
    {
        "updated_at": "2019-02-12T16:36:59.000Z",
        "text": null,
        "option": {
            "id": 8,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "name": "interior_breast_pocket_r",
            "description": "Interior Breast Pocket (R)",
            "gerber_option": true,
            "option_operator": "A1",
            "option_group_id": 2,
            "material_type_id": 0,
            "option_location": "interior",
            "option_control_type": "select",
            "popup_text": "Cellphone Pocket: Right and Pen/Pencil Pocket: Right cannot be ordered with Interior Breast Pocket (R): Double Besom Button-Through\nIf Interior Breast Pocket R: Patch Pockets are chosen, Interior Shape: Parallel is required\nShell Fabric Pocket Fasteners are only available on Interior Breast Pockets with Loop, Flap, or Tab",
            "parent_option_id": null,
            "display_order": 2,
            "active": true
        },
        "option_value": {
            "id": 1357,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "option_value": "double_besom",
            "gerber_optval": true,
            "rc_price": "0.0",
            "premium_id": 1,
            "default_value": true,
            "copyable": true,
            "display_order": 2,
            "active": true,
            "description": "Double Besom"
        }
    },
    {
        "updated_at": "2019-02-12T16:36:59.000Z",
        "text": null,
        "option": {
            "id": 9,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "name": "pen_pencil_pocket",
            "description": "Pen/Pencil Pocket",
            "gerber_option": true,
            "option_operator": "A1",
            "option_group_id": 2,
            "material_type_id": 0,
            "option_location": "interior",
            "option_control_type": "select",
            "popup_text": "Interior Breast Pocket: Double Besom Button-Through cannot be ordered with Pen/Pencil Pocket",
            "parent_option_id": null,
            "display_order": 6,
            "active": true
        },
        "option_value": {
            "id": 32,
            "garment_type": 33,
            "tailoring_grade": 863,
            "order_type": 3,
            "option_value": "none",
            "gerber_optval": false,
            "rc_price": "0.0",
            "premium_id": 1,
            "default_value": true,
            "copyable": true,
            "display_order": 1,
            "active": true,
            "description": "None"
        }
    },
    {
        "updated_at": "2019-02-12T16:36:59.000Z",
        "text": null,
        "option": {
            "id": 10,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "name": "cellphone_pocket",
            "description": "Cell Phone Pocket",
            "gerber_option": true,
            "option_operator": "A1",
            "option_group_id": 2,
            "material_type_id": 0,
            "option_location": "interior",
            "option_control_type": "select",
            "popup_text": "Interior Breast Pocket: Double Besom Button-Through cannot be ordered with Cellphone Pocket\nInterior Shape: Curved French Facing Two-Piece is not available when Cellphone Pocket is chosen",
            "parent_option_id": null,
            "display_order": 5,
            "active": true
        },
        "option_value": {
            "id": 33,
            "garment_type": 33,
            "tailoring_grade": 351,
            "order_type": 3,
            "option_value": "right",
            "gerber_optval": true,
            "rc_price": "0.0",
            "premium_id": 1,
            "default_value": false,
            "copyable": true,
            "display_order": 3,
            "active": true,
            "description": "Right"
        }
    },
    {
        "updated_at": "2019-02-12T16:36:59.000Z",
        "text": null,
        "option": {
            "id": 11,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "name": "lower_card_pocket_l",
            "description": "Lower Card Pocket (L)",
            "gerber_option": true,
            "option_operator": "A1",
            "option_group_id": 2,
            "material_type_id": 0,
            "option_location": "interior",
            "option_control_type": "select",
            "popup_text": null,
            "parent_option_id": null,
            "display_order": 7,
            "active": true
        },
        "option_value": {
            "id": 1403,
            "garment_type": 33,
            "tailoring_grade": 351,
            "order_type": 3,
            "option_value": "none",
            "gerber_optval": false,
            "rc_price": "0.0",
            "premium_id": 1,
            "default_value": true,
            "copyable": true,
            "display_order": 1,
            "active": true,
            "description": "None"
        }
    },
    {
        "updated_at": "2019-02-12T16:36:59.000Z",
        "text": null,
        "option": {
            "id": 12,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "name": "lower_card_pocket_r",
            "description": "Lower Card Pocket (R)",
            "gerber_option": true,
            "option_operator": "A1",
            "option_group_id": 2,
            "material_type_id": 0,
            "option_location": "interior",
            "option_control_type": "select",
            "popup_text": null,
            "parent_option_id": null,
            "display_order": 8,
            "active": true
        },
        "option_value": {
            "id": 1411,
            "garment_type": 33,
            "tailoring_grade": 351,
            "order_type": 3,
            "option_value": "none",
            "gerber_optval": false,
            "rc_price": "0.0",
            "premium_id": 1,
            "default_value": true,
            "copyable": true,
            "display_order": 1,
            "active": true,
            "description": "None"
        }
    },
    {
        "updated_at": "2019-02-12T16:36:59.000Z",
        "text": null,
        "option": {
            "id": 13,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "name": "contrast_pocket_cording",
            "description": "Contrast Pocket Cording",
            "gerber_option": true,
            "option_operator": "A1",
            "option_group_id": 2,
            "material_type_id": 2,
            "option_location": "interior",
            "option_control_type": "select",
            "popup_text": "Ribbon cannot be used for Contrast Pocket Cording. Please use ONLY Shirt Trim or Lining fabrics for this option.",
            "parent_option_id": null,
            "display_order": 15,
            "active": true
        },
        "option_value": {
            "id": 41,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "option_value": "shell_fabric",
            "gerber_optval": false,
            "rc_price": "0.0",
            "premium_id": 1,
            "default_value": true,
            "copyable": true,
            "display_order": 2,
            "active": true,
            "description": "Use Shell Fabric"
        }
    },
    {
        "updated_at": "2019-02-12T16:36:59.000Z",
        "text": null,
        "option": {
            "id": 14,
            "garment_type": 33,
            "tailoring_grade": 895,
            "order_type": 3,
            "name": "exterior_lapel_stitching",
            "description": "Collar/Lapels/Front Stitching",
            "gerber_option": false,
            "option_operator": "B6",
            "option_group_id": 3,
            "material_type_id": 0,
            "option_location": "exterior",
            "option_control_type": "select",
            "popup_text": null,
            "parent_option_id": null,
            "display_order": 3,
            "active": true
        },
        "option_value": {
            "id": 918,
            "garment_type": 33,
            "tailoring_grade": 383,
            "order_type": 3,
            "option_value": "pic_1_4",
            "gerber_optval": false,
            "rc_price": "0.0",
            "premium_id": 1,
            "default_value": false,
            "copyable": true,
            "display_order": 6,
            "active": true,
            "description": "1/4\" Pic Stitch"
        }
    }
]
```

Returns an array of garment options and option values for a specific garment.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/garments/:id/options`

### Query Parameters

| Parameter | Default | Description                                              |
| --------- | ------- | -------------------------------------------------------- |
| id        | N/A     | The specific garment id you want to see the options for. |

### Other

- Permissions: All
- Pagination: N/A

## Get All Garment Measurements

```shell
curl "https://api.trinity-apparel.com/v1/garments/890682/measurements"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "updated_at": "2018-08-10T21:29:27.000Z",
        "text": "0.000",
        "measurement": {
            "id": 7,
            "name": "perkins_incline",
            "description": "Incline Reading",
            "description_zh_cn": "正常",
            "garment_type": 239,
            "tailoring_grade": 511,
            "isdropdown": 0,
            "display_order": 5
        },
        "measurement_value": {
            "id": 16,
            "value": "0.000",
            "description": "",
            "description_zh_cn": "",
            "default_value": 1,
            "display_order": 1,
            "active": 1
        }
    },
    {
        "updated_at": "2018-08-10T21:29:27.000Z",
        "text": "0.000",
        "measurement": {
            "id": 9,
            "name": "perkins_shoulder_l",
            "description": "Shoulder Reading (L)",
            "description_zh_cn": "正常",
            "garment_type": 239,
            "tailoring_grade": 511,
            "isdropdown": 0,
            "display_order": 6
        },
        "measurement_value": {
            "id": 39,
            "value": "0.000",
            "description": "",
            "description_zh_cn": "",
            "default_value": 1,
            "display_order": 1,
            "active": 1
        }
    },
    {
        "updated_at": "2018-08-10T21:29:27.000Z",
        "text": "0.000",
        "measurement": {
            "id": 10,
            "name": "perkins_shoulder_r",
            "description": "Shoulder Reading (R)",
            "description_zh_cn": "正常",
            "garment_type": 239,
            "tailoring_grade": 511,
            "isdropdown": 0,
            "display_order": 7
        },
        "measurement_value": {
            "id": 51,
            "value": "0.000",
            "description": "",
            "description_zh_cn": "",
            "default_value": 1,
            "display_order": 1,
            "active": 1
        }
    },
    {
        "updated_at": "2018-08-10T21:29:27.000Z",
        "text": "regular",
        "measurement": {
            "id": 11,
            "name": "perkins_shoulder_desc_l",
            "description": "Shoulder Desc (L)",
            "description_zh_cn": "",
            "garment_type": 239,
            "tailoring_grade": 1023,
            "isdropdown": 0,
            "display_order": 8
        },
        "measurement_value": {
            "id": 65,
            "value": "regular",
            "description": "Regular",
            "description_zh_cn": "正常",
            "default_value": 1,
            "display_order": 3,
            "active": 1
        }
    },
    {
        "updated_at": "2018-08-10T21:29:27.000Z",
        "text": "regular",
        "measurement": {
            "id": 12,
            "name": "perkins_shoulder_desc_r",
            "description": "Shoulder Desc (R)",
            "description_zh_cn": "",
            "garment_type": 239,
            "tailoring_grade": 1023,
            "isdropdown": 0,
            "display_order": 9
        },
        "measurement_value": {
            "id": 71,
            "value": "regular",
            "description": "Regular",
            "description_zh_cn": "正常",
            "default_value": 1,
            "display_order": 3,
            "active": 1
        }
    },
    {
        "updated_at": "2018-08-10T21:29:27.000Z",
        "text": "42",
        "measurement": {
            "id": 49,
            "name": "shirt_chest_base",
            "description": "Actual Chest",
            "description_zh_cn": "净胸围",
            "garment_type": 8,
            "tailoring_grade": 453,
            "isdropdown": 1,
            "display_order": 5
        },
        "measurement_value": null
    },
    {
        "updated_at": "2018-08-10T21:29:27.000Z",
        "text": "5",
        "measurement": {
            "id": 50,
            "name": "shirt_chest_fit",
            "description": "Chest Fit Allowance",
            "description_zh_cn": "胸围加放量",
            "garment_type": 8,
            "tailoring_grade": 453,
            "isdropdown": 0,
            "display_order": 6
        },
        "measurement_value": null
    },
    {
        "updated_at": "2018-08-10T21:29:27.000Z",
        "text": "47",
        "measurement": {
            "id": 51,
            "name": "shirt_chest_total",
            "description": "Chest Fit Total",
            "description_zh_cn": "胸围",
            "garment_type": 8,
            "tailoring_grade": 453,
            "isdropdown": 1,
            "display_order": 7
        },
        "measurement_value": null
    },
    {
        "updated_at": "2018-08-10T21:29:27.000Z",
        "text": "0",
        "measurement": {
            "id": 54,
            "name": "shirt_waist_total",
            "description": "Waist Fit Total",
            "description_zh_cn": "腰围",
            "garment_type": 8,
            "tailoring_grade": 453,
            "isdropdown": 1,
            "display_order": 10
        },
        "measurement_value": null
    },
    {
        "updated_at": "2018-08-10T21:29:27.000Z",
        "text": "0",
        "measurement": {
            "id": 57,
            "name": "shirt_hips_total",
            "description": "Hips Fit Total",
            "description_zh_cn": "摆围",
            "garment_type": 8,
            "tailoring_grade": 453,
            "isdropdown": 1,
            "display_order": 13
        },
        "measurement_value": null
    },
    {
        "updated_at": "2018-08-10T21:29:27.000Z",
        "text": "regular",
        "measurement": {
            "id": 58,
            "name": "shirt_armhole",
            "description": "Armhole/Sleeve Fit",
            "description_zh_cn": "",
            "garment_type": 8,
            "tailoring_grade": 453,
            "isdropdown": 0,
            "display_order": 14
        },
        "measurement_value": {
            "id": 13,
            "value": "regular",
            "description": "Regular",
            "description_zh_cn": "袖笼正常",
            "default_value": 1,
            "display_order": 1,
            "active": 1
        }
    },
    {
        "updated_at": "2018-08-10T21:29:28.000Z",
        "text": "0",
        "measurement": {
            "id": 98,
            "name": "shirt_point_sleeve_l",
            "description": "Shoulder Point Sleeve Length (L)",
            "description_zh_cn": "直袖长 (左)",
            "garment_type": 8,
            "tailoring_grade": 453,
            "isdropdown": 0,
            "display_order": 0
        },
        "measurement_value": null
    },
    {
        "updated_at": "2018-08-10T21:29:28.000Z",
        "text": "0",
        "measurement": {
            "id": 99,
            "name": "shirt_point_sleeve_r",
            "description": "Shoulder Point Sleeve Length (R)",
            "description_zh_cn": "直袖长 (右)",
            "garment_type": 8,
            "tailoring_grade": 453,
            "isdropdown": 0,
            "display_order": 0
        },
        "measurement_value": null
    },
    {
        "updated_at": "2018-08-10T21:29:28.000Z",
        "text": "regular",
        "measurement": {
            "id": 122,
            "name": "gerber_armhole",
            "description": "Gerber Armhole",
            "description_zh_cn": null,
            "garment_type": 239,
            "tailoring_grade": 447,
            "isdropdown": 0,
            "display_order": 0
        },
        "measurement_value": null
    },
    {
        "updated_at": "2018-08-10T21:29:27.000Z",
        "text": "normal",
        "measurement": {
            "id": 123,
            "name": "posture",
            "description": "Posture",
            "description_zh_cn": null,
            "garment_type": 43,
            "tailoring_grade": 1023,
            "isdropdown": 0,
            "display_order": 12
        },
        "measurement_value": {
            "id": 184,
            "value": "normal",
            "description": "Normal",
            "description_zh_cn": "正常",
            "default_value": 1,
            "display_order": 1,
            "active": 1
        }
    },
    {
        "updated_at": "2018-08-10T21:29:27.000Z",
        "text": "normal",
        "measurement": {
            "id": 130,
            "name": "stomach_stature",
            "description": "Stomach Description",
            "description_zh_cn": null,
            "garment_type": 43,
            "tailoring_grade": 447,
            "isdropdown": 0,
            "display_order": 19
        },
        "measurement_value": {
            "id": 214,
            "value": "normal",
            "description": "Normal",
            "description_zh_cn": null,
            "default_value": 1,
            "display_order": 1,
            "active": 1
        }
    },
    {
        "updated_at": "2018-08-10T21:29:28.000Z",
        "text": "normal",
        "measurement": {
            "id": 185,
            "name": "gerber_posture_shirt",
            "description": "Gerber Posture (Shirt)",
            "description_zh_cn": null,
            "garment_type": 8,
            "tailoring_grade": 389,
            "isdropdown": 0,
            "display_order": 0
        },
        "measurement_value": {
            "id": 440,
            "value": "normal",
            "description": "Normal",
            "description_zh_cn": null,
            "default_value": 0,
            "display_order": 0,
            "active": 1
        }
    },
    {
        "updated_at": "2018-08-10T21:29:28.000Z",
        "text": "fold",
        "measurement": {
            "id": 220,
            "name": "gerber_layout",
            "description": "Gerber Layout",
            "description_zh_cn": null,
            "garment_type": 33,
            "tailoring_grade": 319,
            "isdropdown": 0,
            "display_order": 0
        },
        "measurement_value": null
    },
    {
        "updated_at": "2018-08-10T21:29:28.000Z",
        "text": "3",
        "measurement": {
            "id": 267,
            "name": "swacket_chest",
            "description": "Chest",
            "description_zh_cn": "胸围",
            "garment_type": 512,
            "tailoring_grade": 383,
            "isdropdown": 0,
            "display_order": 0
        },
        "measurement_value": null
    },
    {
        "updated_at": "2018-08-10T21:29:27.000Z",
        "text": "none",
        "measurement": {
            "id": 271,
            "name": "shirt_elbow_forearm_reduction",
            "description": "Elbow/Forearm Reduction",
            "description_zh_cn": "手肘围减",
            "garment_type": 8,
            "tailoring_grade": 453,
            "isdropdown": 0,
            "display_order": 15
        },
        "measurement_value": {
            "id": 602,
            "value": "none",
            "description": "None",
            "description_zh_cn": "Shirt Elbow Forearm Fit Regular",
            "default_value": 1,
            "display_order": 1,
            "active": 1
        }
    },
    {
        "updated_at": "2018-08-10T21:29:28.000Z",
        "text": "-0.5",
        "measurement": {
            "id": 278,
            "name": "estimated_finished_thigh",
            "description": "Estimated Finished Thigh",
            "description_zh_cn": null,
            "garment_type": 196,
            "tailoring_grade": 319,
            "isdropdown": 0,
            "display_order": 8
        },
        "measurement_value": null
    },
    {
        "updated_at": "2018-08-10T21:29:28.000Z",
        "text": "-0.5",
        "measurement": {
            "id": 279,
            "name": "estimated_u_rise",
            "description": "Estimated U Rise",
            "description_zh_cn": null,
            "garment_type": 196,
            "tailoring_grade": 383,
            "isdropdown": 0,
            "display_order": 5
        },
        "measurement_value": null
    }
]
```

Returns an array of garment measurements and measurement values for a specific garment.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/garments/:id/measurements`

### Query Parameters

| Parameter | Default | Description                                                   |
| --------- | ------- | ------------------------------------------------------------- |
| id        | N/A     | The specific garment id you want to see the measurements for. |

### Other

- Permissions: All
- Pagination: N/A

## Get Order Statuses

```shell
curl "https://api.trinity-apparel.com/v1/order_statuses"
  -H "Authorization Bearer: swaledale"
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
  -H "Authorization Bearer: swaledale"
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

| Parameter | Default | Description                    |
| --------- | ------- | ------------------------------ |
| code      | N/A     | The specific order status code |

### Other

- Permissions: All
- Pagination: N/A

## Get Delay Statuses

```shell
curl "https://api.trinity-apparel.com/v1/delay_statuses"
  -H "Authorization Bearer: swaledale"
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
  -H "Authorization Bearer: swaledale"
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

| Parameter | Default | Description                    |
| --------- | ------- | ------------------------------ |
| code      | N/A     | The specific delay status code |

### Other

- Permissions: All
- Pagination: N/A