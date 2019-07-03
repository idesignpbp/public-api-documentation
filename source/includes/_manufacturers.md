# Manufacturers API

The manufacturers API allows a factory to download all relevant information needed to produce a garment.

Part of the Manufacturers API

## Resources

The resources provided by the manufacturers API are almost identical to the orders API.

### Garment

```json
# Standard Object - Used in a resource collection
{
    "id": 846718,
    "title": "TEST-846718",
    "order_id": 386627,
    "copied_garment_id": null,
    "price": "100.0",
    "option_cost": "0.0",
    "garment_type": "CT",
    "created_at": "2018-04-26T17:50:31.000Z",
    "updated_at": null,
    "prefix": "TEST",
    "index": "",
    "last_status_change_date": "2018-04-26T17:50:31.000Z",
    "last_delay_change_date": null,
    "links": {
        "gerber": "http://localhost:8080/share/order_insert.php?suit_ids[]=846718&units=uscust&format=gerber&fabtype=both",
        "order_insert": "https://trinity-apparel.com/share/order_insert.php?format=pdfzip&units=si&suit_ids%5B%5D=846718",
        "order_split": "https://documents.trinity-apparel.com/order_splits?garment_id=846718&locale=en"
    },
    "order_status": ...,
    "delay_status": ...,
    "dealer_order": ...,
    "manufacturer": ...,
    "fabric": ...
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


## Get All Buttons

```shell
curl "https://api.trinity-apparel.com/v1/buttons"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "value": "KYKW023_Tan",
        "description": "2-10 Tan Marbled Premium",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-10_Tan_Marbled_Premium?wid=100",
        "rgb": "107,96,72",
        "display_order": 31,
        "active": 1
    },
    {
        "value": "KYKW024_Cinnamon",
        "description": "2-11 Cinnamon Marbled Premium",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-11_Cinnamon_Marbled_Premium?wid=100",
        "rgb": "115,76,62",
        "display_order": 32,
        "active": 1
    },
    {
        "value": "KYKW025_Taupe",
        "description": "2-12 Taupe Marbled Premium",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-12_Taupe_Marbled_Premium?wid=100",
        "rgb": "99,93,69",
        "display_order": 33,
        "active": 1
    },
    {
        "value": "KYKW026_Grey",
        "description": "2-02 Grey Marbled Premium",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-02_Grey_Marbled_Premium?wid=100",
        "rgb": "79,79,76",
        "display_order": 34,
        "active": 1
    },
    {
        "value": "KYKW027_Dark_Brown",
        "description": "2-13 Dark Brown Marbled Premium",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-13_Dark_Brown_Marbled_Premium?wid=100",
        "rgb": "46,36,23",
        "display_order": 35,
        "active": 1
    },
    {
        "value": "KYKW028_Charcoal",
        "description": "2-03 Charcoal Marbled Premium",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-03_Charcoal_Marbled_Premium?wid=100",
        "rgb": "50,50,50",
        "display_order": 36,
        "active": 1
    },
    {
        "value": "KYKW022_Black",
        "description": "2-04 Black Marbled Premium",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-04_Black_Marbled_Premium?wid=100",
        "rgb": "43,43,43",
        "display_order": 30,
        "active": 1
    },
    {
        "value": "KW017_Shield",
        "description": "2-23 Shield Premium",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-23_Shield_Premium?wid=100",
        "rgb": "43,43,43",
        "display_order": 28,
        "active": 1
    },
    {
        "value": "KW018_Skull",
        "description": "2-24 Skull Premium",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-24_Skull_Premium?wid=100",
        "rgb": "157,157,157",
        "display_order": 29,
        "active": 1
    },
    {
        "value": "KB002_White_MOP",
        "description": "1-31 White Mother of Pearl",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-31_White_Mother_of_Pearl?wid=100",
        "rgb": "233,235,226",
        "display_order": 17,
        "active": 1
    },
    {
        "value": "KB001_Smoke_MOP",
        "description": "1-32 Smoke Mother of Pearl",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-32_Smoke_Mother_of_Pearl?wid=100",
        "rgb": "46,58,73",
        "display_order": 18,
        "active": 1
    },
    {
        "value": "KG036_Navy",
        "description": "1-08 Navy",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-08_Navy?wid=100",
        "rgb": "37,37,49",
        "display_order": 5,
        "active": 1
    },
    {
        "value": "KG038_Dark_Taupe",
        "description": "1-25 Dark Taupe",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-25_Dark_Taupe?wid=100",
        "rgb": "69,45,42",
        "display_order": 6,
        "active": 1
    },
    {
        "value": "KG051_Ivory",
        "description": "1-18 Ivory",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-18_Ivory?wid=100",
        "rgb": "254,235,179",
        "display_order": 8,
        "active": 1
    },
    {
        "value": "KG052_Coffee",
        "description": "1-22 Coffee",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-22_Coffee?wid=100",
        "rgb": "107,81,45",
        "display_order": 9,
        "active": 1
    },
    {
        "value": "KG039_Charcoal_Grey",
        "description": "1-05 Charcoal Gray",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-05_Charcoal_Gray?wid=100",
        "rgb": "77,75,75",
        "display_order": 4,
        "active": 1
    },
    {
        "value": "KG041_Sand",
        "description": "1-19 Sand",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-19_Sand?wid=100",
        "rgb": "185,160,120",
        "display_order": 7,
        "active": 1
    },
    {
        "value": "KG056_Caramel",
        "description": "1-20 Caramel",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-20_Caramel?wid=100",
        "rgb": "133,109,72",
        "display_order": 10,
        "active": 1
    },
    {
        "value": "KG062_Tan",
        "description": "1-21 Tan",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-21_Tan?wid=100",
        "rgb": "130,86,31",
        "display_order": 11,
        "active": 1
    },
    {
        "value": "KG064_Medium_Brown",
        "description": "1-23 Medium Brown",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-23_Medium_Brown?wid=100",
        "rgb": "85,60,36",
        "display_order": 12,
        "active": 1
    },
    {
        "value": "KG069_Dark_Brown",
        "description": "1-24 Dark Brown",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-24_Dark_Brown?wid=100",
        "rgb": "50,34,18",
        "display_order": 13,
        "active": 1
    },
    {
        "value": "KG019_Black",
        "description": "1-06 Black",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-06_Black?wid=100",
        "rgb": "43,43,43",
        "display_order": 3,
        "active": 1
    },
    {
        "value": "KNJ011_Dark_Brown",
        "description": "1-30 Dark Brown Horn",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-30_Dark_Brown_Horn?wid=100",
        "rgb": "33,35,32",
        "display_order": 14,
        "active": 1
    },
    {
        "value": "KNJ012_Medium_Brown",
        "description": "1-28 Medium Brown Horn",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-28_Medium_Brown_Horn?wid=100",
        "rgb": "72,52,31",
        "display_order": 15,
        "active": 1
    },
    {
        "value": "KNJ014_Rust_Brown",
        "description": "1-29 Rust Brown Horn",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-29_Rust_Brown_Horn?wid=100",
        "rgb": "93,44,35",
        "display_order": 16,
        "active": 1
    }
]
```

Returns an array of active buttons.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/buttons`

### Query Parameters

| Parameter       | Default | Description                                                       |
| --------------- | ------- | ----------------------------------------------------------------- |
| show_archived   | false   | If set to true, the result will also include inactive buttons.    |
| description     | N/A     | If set, will return any buttons with exact matching descriptions. |
| q               | N/A     | If set, return all fuzzy matched descriptions.                    |
| option_value_id | N/A     | If set, returns all valid buttons for that option value.          |

### Other

- Permissions: All
- Pagination: Yes

### Querying by multiple button descriptions

In order to query for multiple buttons, you will pass in multiple params with the format like below:

`GET https://api.trinity-apparel.com/v1/buttons?description[]=2-10 Tan Marbled Premium&description[]=2-12 Taupe Marbled Premium&description[]=2-04 Black Marbled Premium`

