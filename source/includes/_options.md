# Options API

## Option Resources

### Option Group

Option groups are the groups/folders that contain styling options for a particular garment in Workflow. There are 30 option groups currently available.

```json
# Standard Object - Used in a resource collection
{
    "id": 27,
    "name": "Label Options",
    "garment_type": 623,
    "display_order": 230
}
```

Standard Attributes

| Attribute                               | Description                                             |
| --------------------------------------- | ------------------------------------------------------- |
| id <br> <span>integer</span>            | Unique identifier for the object.                       |
| name <br> <span>string</span>           | The name of the option group.                           |
| garment_type <br> <span>integer</span>   | A bitmask for option availability by garment type. [Click here](#advanced-fabric-queries) for more info |
| display_order <br> <span>integer</span> | The order in which the option group is displayed in Workflow. |

### Option

A styling option for a garment.  Typically these are set to an option value, a fabric number, or a text field.  There are 600+ options currently available.

```json
# Standard Object - Used in a resource collection
{
    "id": 1,
    "name": "garment_label",
    "description": "Garment Label",
    "display_order": 5,
    "garment_type": 545,
    "option_location": "interior",
    "active": true,
    "option_group": ...
}
```

Standard Attributes

| Attribute                               | Description                                             |
| --------------------------------------- | ------------------------------------------------------- |
| id <br> <span>integer</span>            | Unique identifier for the object.                       |
| name <br> <span>string</span>           | The name of the option.                                 |
| description <br> <span>string</span>    | A human readable description of the option.             |
| display_order <br> <span>integer</span> | The order in which the option is displayed in Workflow. |
| garment_type <br> <span>integer</span>  | A bitmask for option availability by garment type. [Click here](#garment-types) for more info |
| location <br> <span>string</span>       | High level grouping for options. Can be materials, interior, or exterior. |
| active <br> <span>boolean</span>        | Is the option currently available for ordering?         |
| option_group <br> <span>subresource</span> | The option is a part of a single option group        |

### Option Value

A choice for a styling option.  Example: a specific thread for sleeve button thread color. There are 11,000 option values currently available.

```json
# Standard Object - Used in a resource collection
{
    "id": 1,
    "option_value": "trinity_label",
    "description": "Trinity Apparel Group",
    "display_order": 3,
    "active": true,
    "garment_type": 545,
    "default_value": false,
    "option": ... ,
    "manufacturer_option_values": [ ... ]
}
```

Standard Attributes

| Attribute                               | Description                                             |
| --------------------------------------- | ------------------------------------------------------- |
| id <br> <span>integer</span>            | Unique identifier for the object.                       |
| name <br> <span>string</span>           | The name of the option.                                 |
| description <br> <span>string</span>    | A human readable description of the option.             |
| display_order <br> <span>integer</span> | The order in which the option is displayed in Workflow. |
| garment_type <br> <span>integer</span>  | A bitmask for option availability by garment type. [Click here](#garment-types) for more info |
| location <br> <span>string</span>       | High level grouping for option values. Can be materials, interior, or exterior. |
| active <br> <span>boolean</span>        | Is the option currently available for ordering?         |
| option <br> <span>subresource</span>    | The option value is a choice for a styling option       | 

### Manufacturer Option Value

Each option has a unique description for each manufacturer.  This allows for language translations and factory specific information such as a button supplier number.

```json
# Standard Object - Used in a resource collection
{
    "id": 17206,
    "locale": "zh",
    "description": "用Trinity商标",
    "chinese_description": "用Trinity商标"
}
```

Standard Attributes

| Attribute                                    | Description                                 |
| -------------------------------------------- | ------------------------------------------- |
| id <br> <span>integer</span>                 | Unique identifier for the object.           |
| locale <br> <span>string</span>              | A two character language code for the translation - [Click here](https://www.science.co.il/language/Locale-codes.php) for more info |
| description <br> <span>string</span>         | Human readable description of the material. |
| chinese_description <br> <span>string</span> | Human readable description of the material. |


## Get All Options

```shell
curl "https://api.trinity-apparel.com/v1/options"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 1,
        "name": "garment_label",
        "description": "Garment Label",
        "display_order": 5,
        "garment_type": 545,
        "location": "interior",
        "active": true,
        "option_group": {
            "id": 27,
            "name": "Label Options",
            "garment_type": 623,
            "display_order": 230
        }
    },
    {
        "id": 2,
        "name": "vent_style",
        "description": "Vent Style",
        "display_order": 1,
        "garment_type": 33,
        "location": "exterior",
        "active": true,
        "option_group": {
            "id": 30,
            "name": "Vent Options",
            "garment_type": 33,
            "display_order": 120
        }
    },
    {
        "id": 3,
        "name": "shoulder_style",
        "description": "Shoulder Style",
        "display_order": 1,
        "garment_type": 33,
        "location": "exterior",
        "active": true,
        "option_group": {
            "id": 29,
            "name": "Shoulder Options",
            "garment_type": 35,
            "display_order": 100
        }
    },
    {
        "id": 4,
        "name": "exterior_breast_pocket",
        "description": "Exterior Breast Pocket",
        "display_order": 1,
        "garment_type": 545,
        "location": "exterior",
        "active": true,
        "option_group": {
            "id": 2,
            "name": "Pocket Options",
            "garment_type": 623,
            "display_order": 140
        }
    },
    ...
]
```

Returns an array of options.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/options`

### Query Parameters

| Parameter       | Default | Description                                                       |
| --------------- | ------- | ----------------------------------------------------------------- |
| active          | N/A     | If set, returns only only active or inactive options.             |
| q               | N/A     | If set, return all fuzzy matched option names and descriptions.   |
| option_group_id | N/A     | If set, will return any buttons with exact matching descriptions. |
| location        | N/A     | If set, returns all options in a specific location (E.g., exterior). |
| garment_type    | N/A     | If set, returns all options that match a garment bitmask (E.g., 2 for Vests). |

### Other

- Permissions: All
- Pagination: Yes

### Example queries

#### Wildcard Search

Ex. Search for options mentioning "milanese"
`GET https://api.trinity-apparel.com/v1/options?q=milanese`

#### Search by Garment Type

Ex. List vest options
`GET https://api.trinity-apparel.com/v1/options?garment_type=2`

#### Search Option Group and Garment Type 

Ex. List pocket options on a shirt
`GET https://api.trinity-apparel.com/v1/options?option_group_id=2&garment_type=8`


## Get a Specific Option

```shell
curl "https://api.trinity-apparel.com/v1/options/229"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
    "id": 229,
    "name": "lining_fabric_num",
    "description": "Lining Fabric #",
    "display_order": 110,
    "garment_type": 33,
    "location": "interior",
    "active": true,
    "option_group": {
        "id": 28,
        "name": "Interior Options",
        "garment_type": 545,
        "display_order": 250
    }
}
```

Returns details on a specific button.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/options/:id`

### Query Parameters

| Parameter | Default | Description                               |
| --------- | ------- | ----------------------------------------- |
| id.       | N/A     | The specific id  you want to see          |

### Other

- Permissions: All
- Pagination: N/A
