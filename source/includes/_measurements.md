# Measurements API

## Measurement Resources

### Measurement Group

Measurement groups are the groups/folders that contain measurements and alterations for a particular garment in Workflow. There are 12 option groups currently available.

```json
# Standard Object - Used in a resource collection
{
    "id": 2,
    "name": "Body Description",
    "garment_type": 239,
    "display_order": 2
}
```

Standard Attributes

| Attribute                               | Description                                             |
| --------------------------------------- | ------------------------------------------------------- |
| id <br> <span>integer</span>            | Unique identifier for the object.                       |
| name <br> <span>string</span>           | The name of the measurement group.                           |
| garment_type <br> <span>integer</span>   | A bitmask for measurement availability by garment type. [Click here](#advanced-fabric-queries) for more info |
| display_order <br> <span>integer</span> | The order in which the measurement group is displayed in Workflow. |

### Measurement

A measurement for a garment.  Typically these are set to a number (inches, pounds, etc) or a choice in a dropdown.  There are over 200 currently available.

```json
# Standard Object - Used in a resource collection
{
    "id": 16,
    "name": "coat_chest",
    "description": "Chest",
    "display_order": 3,
    "chinese_description": "胸围",
    "garment_type": 33,
    "convunit": 1,
    "required": true,
    "active": 1,
    "measurement_group": ...
}
```

Standard Attributes

| Attribute                               | Description                                             |
| --------------------------------------- | ------------------------------------------------------- |
| id <br> <span>integer</span>            | Unique identifier for the object.                       |
| name <br> <span>string</span>           | The name of the measurement.                                 |
| description <br> <span>string</span>    | A human readable description of the measurement.             |
| chinese_description <br> <span>string</span>    | A Chinese description of the measurement.             |
| display_order <br> <span>integer</span> | The order in which the measurement is displayed in Workflow. |
| garment_type <br> <span>integer</span>  | A bitmask for measurement availability by garment type. [Click here](#garment-types) for more info |
| convunit <br> <span>boolean</span>      | Should this measurement be converted from inches to centimeters, etc?         |
| required <br> <span>boolean</span>      | Is the measurement required when ordering?         |
| active <br> <span>boolean</span>        | Is the measurement currently available for ordering?         |
| measurement_group <br> <span>subresource</span> | The measurement is a part of a single measurement group        |

### Measurement Value

A choice for a measurement.  Example: the degree of sloping for posture. There are over 500 measurement values currently available.

```json
# Standard Object - Used in a resource collection
{
    "id": 2,
    "value": "sloping",
    "description": "Sloping",
    "display_order": 2,
    "measurement": ...
}
```

Standard Attributes

| Attribute                               | Description                                             |
| --------------------------------------- | ------------------------------------------------------- |
| id <br> <span>integer</span>            | Unique identifier for the object.                       |
| value <br> <span>string</span>          | The system value for the measurement selection.         |
| description <br> <span>string</span>    | A human readable description of the measurement value.  |
| display_order <br> <span>integer</span> | The order in which the measurement value is displayed in Workflow. |
| measurement <br> <span>subresource</span>    | The measurement value is a choice for a measurement | 


## Get All Option Groups

```shell
curl "https://api.trinity-apparel.com/v1/option_groups"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 33,
        "name": "Inactive Options",
        "garment_type": 255,
        "display_order": 10
    },
    {
        "id": 40,
        "name": "Construction",
        "garment_type": 33,
        "display_order": 20
    },
    {
        "id": 39,
        "name": "Materials",
        "garment_type": 751,
        "display_order": 30
    },
    {
        "id": 25,
        "name": "Formal Options",
        "garment_type": 5,
        "display_order": 40
    },
    {
        "id": 15,
        "name": "Collar Options",
        "garment_type": 8,
        "display_order": 50
    },
    {
        "id": 1,
        "name": "Collar/Lapel Options",
        "garment_type": 547,
        "display_order": 60
    },
    {
        "id": 41,
        "name": "Front Options",
        "garment_type": 4,
        "display_order": 70
    },
    {
        "id": 42,
        "name": "Vest Front Options",
        "garment_type": 2,
        "display_order": 80
    },
    {
        "id": 9,
        "name": "Waistband Options",
        "garment_type": 196,
        "display_order": 90
    },
    ...
]
```

Returns an array of option groups.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/option_groups`

### Query Parameters

| Parameter       | Default | Description                                                       |
| --------------- | ------- | ----------------------------------------------------------------- |
| garment_type    | N/A     | If set, returns all options that match a garment bitmask (E.g., 2 for Vests). |

### Other

- Permissions: N/A
- Pagination: No


## Get a Specific Option Group

```shell
curl "https://api.trinity-apparel.com/v1/option_groups/4"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
    "id": 4,
    "name": "Button/Buttonhole Options",
    "garment_type": 751,
    "display_order": 170
}
```

Returns details on a specific option group.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/option_groups/:id`

### Query Parameters

| Parameter | Default | Description                               |
| --------- | ------- | ----------------------------------------- |
| id.       | N/A     | The specific id you want to see           |

### Other

- Permissions: N/A
- Pagination: N/A


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

- Permissions: N/A
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
| id.       | N/A     | The specific id you want to see           |

### Other

- Permissions: N/A
- Pagination: N/A


## Get All Option Values

```shell
curl "https://api.trinity-apparel.com/v1/option_values"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 1,
        "option_value": "trinity_label",
        "description": "Trinity Apparel Group",
        "display_order": 3,
        "active": true,
        "garment_type": 545,
        "default_value": false,
        "option": {
            "id": 1,
            "name": "garment_label",
            "description": "Garment Label",
            "display_order": 5
        },
        "manufacturer_option_values": [
            {
                "id": 1,
                "locale": "zh",
                "description": "用Trinity 集团的布标",
                "chinese_description": "用Trinity 集团的布标"
            },
            {
                "id": 2,
                "locale": "zh",
                "description": "用Trinity 集团的布标",
                "chinese_description": "用Trinity 集团的布标"
            },
            {
                "id": 17206,
                "locale": "zh",
                "description": "用Trinity商标",
                "chinese_description": "用Trinity商标"
            }
        ]
    },
    ...,
    {
        "id": 4,
        "option_value": "no_label",
        "description": "No Label",
        "display_order": 2,
        "active": true,
        "garment_type": 545,
        "default_value": true,
        "option": {
            "id": 1,
            "name": "garment_label",
            "description": "Garment Label",
            "display_order": 5
        },
        "manufacturer_option_values": [
            {
                "id": 4,
                "locale": "zh",
                "description": "不使用布标",
                "chinese_description": "不使用布标"
            },
            {
                "id": 5,
                "locale": "zh",
                "description": "不使用布标",
                "chinese_description": "不使用布标"
            },
            {
                "id": 17207,
                "locale": "zh",
                "description": "无商标",
                "chinese_description": "无商标"
            },
            {
                "id": 26438,
                "locale": "id",
                "description": "No Customer Brand Label",
                "chinese_description": "No Label"
            }
        ]
    },
    {
        "id": 5,
        "option_value": "none",
        "description": "None",
        "display_order": 1,
        "active": true,
        "garment_type": 1,
        "default_value": false,
        "option": {
            "id": 2,
            "name": "vent_style",
            "description": "Vent Style",
            "display_order": 1
        },
        "manufacturer_option_values": [
            {
                "id": 7,
                "locale": "zh",
                "description": "无开叉",
                "chinese_description": "无开叉"
            },
            {
                "id": 8,
                "locale": "zh",
                "description": "无开叉",
                "chinese_description": "无开叉"
            },
            {
                "id": 17208,
                "locale": "zh",
                "description": "无开叉",
                "chinese_description": "无开叉"
            }
        ]
    },
    ...
]
```

Returns an array of option values.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/option_values`

### Query Parameters

| Parameter       | Default | Description                                                       |
| --------------- | ------- | ----------------------------------------------------------------- |
| active          | N/A     | If set, returns only only active or inactive options.             |
| q               | N/A     | If set, return all fuzzy matched option names and descriptions.   |
| option_id       | N/A     | If set, will return any buttons with exact matching descriptions. |
| garment_type    | N/A     | If set, returns all options that match a garment bitmask (E.g., 2 for Vests). |

### Other

- Permissions: N/A
- Pagination: Yes

### Example queries

#### Wildcard Search

Ex. Search for option values mentioning "buckle"

`GET https://api.trinity-apparel.com/v1/option_values?q=buckle`

#### Search by Garment Type

Ex. List topcoat option values

`GET https://api.trinity-apparel.com/v1/option_values?garment_type=32`

#### Search by Option

Ex. List all values for Exterior Breast Pocket 

`GET https://api.trinity-apparel.com/v1/option_values?option_id=4`

#### Wildcard Search and Garment Type 

Ex. List jacket option values that mentioning "ticket"

`GET https://api.trinity-apparel.com/v1/option_values?q=ticket&garment_type=1`


## Get a Specific Option Value

```shell
curl "https://api.trinity-apparel.com/v1/option_values/10"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
    "id": 10,
    "option_value": "welt",
    "description": "Welt (Standard)",
    "display_order": 2,
    "active": true,
    "garment_type": 545,
    "default_value": true,
    "option": {
        "id": 4,
        "name": "exterior_breast_pocket",
        "description": "Exterior Breast Pocket",
        "display_order": 1
    },
    "manufacturer_option_values": [
        {
            "id": 22,
            "locale": "zh",
            "description": "胸袋－内插袋",
            "chinese_description": "胸袋－内插袋"
        },
        {
            "id": 23,
            "locale": "zh",
            "description": "胸袋－内插袋",
            "chinese_description": "胸袋－内插袋"
        },
        {
            "id": 17213,
            "locale": "zh",
            "description": "手巾兜-标准",
            "chinese_description": "手巾兜-标准"
        },
        {
            "id": 26238,
            "locale": "id",
            "description": "OB Welt",
            "chinese_description": null
        }
    ]
}
```

Returns details on a specific option value, which include both the parent options and manufacturer descriptions.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/option_values/:id`

### Query Parameters

| Parameter | Default | Description                               |
| --------- | ------- | ----------------------------------------- |
| id.       | N/A     | The specific id you want to see           |

### Other

- Permissions: N/A
- Pagination: N/A
