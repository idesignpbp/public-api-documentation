# Measurements API

## Measurement Resources

### Measurement Group

Measurement groups are the groups/folders that contain measurements and alterations for a particular garment in Workflow. There are 12 measurement groups currently available.

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


## Get All Measurement Groups

```shell
curl "https://api.trinity-apparel.com/v1/measurement_groups"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 1,
        "name": "General",
        "garment_type": 239,
        "display_order": 1
    },
    {
        "id": 2,
        "name": "Body Description",
        "garment_type": 239,
        "display_order": 2
    },
    {
        "id": 3,
        "name": "Coat",
        "garment_type": 35,
        "display_order": 3
    },
    {
        "id": 4,
        "name": "Vest",
        "garment_type": 2,
        "display_order": 4
    },
    {
        "id": 5,
        "name": "Pant",
        "garment_type": 231,
        "display_order": 5
    },
    {
        "id": 6,
        "name": "Shirt",
        "garment_type": 8,
        "display_order": 6
    },
    {
        "id": 7,
        "name": "Coat Alterations",
        "garment_type": 33,
        "display_order": 7
    },
    {
        "id": 8,
        "name": "Pant Alterations",
        "garment_type": 196,
        "display_order": 9
    },
    {
        "id": 9,
        "name": "Shirt Alterations",
        "garment_type": 8,
        "display_order": 10
    },
    {
        "id": 10,
        "name": "Vest Alterations",
        "garment_type": 2,
        "display_order": 8
    },
    {
        "id": 11,
        "name": "Swacket",
        "garment_type": 512,
        "display_order": 11
    },
    {
        "id": 12,
        "name": "Topcoat",
        "garment_type": 32,
        "display_order": 1
    }
]
```

Returns an array of measurement groups.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/measurement_groups`

### Query Parameters

| Parameter       | Default | Description                                                       |
| --------------- | ------- | ----------------------------------------------------------------- |
| garment_type    | N/A     | If set, returns all measurement groups that match a garment bitmask (E.g., 2 for Vests). |

### Other

- Permissions: N/A
- Pagination: No


## Get a Specific Measurement Group

```shell
curl "https://api.trinity-apparel.com/v1/measurement_groups/4"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
    "id": 3,
    "name": "Coat",
    "garment_type": 35,
    "display_order": 3
}
```

Returns details on a specific measurement group.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/measurement_groups/:id`

### Query Parameters

| Parameter | Default | Description                               |
| --------- | ------- | ----------------------------------------- |
| id.       | N/A     | The specific id you want to see           |

### Other

- Permissions: N/A
- Pagination: N/A


## Get All Measurements

```shell
curl "https://api.trinity-apparel.com/v1/measurements"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    ...,
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
        "measurement_group": {
            "id": 3,
            "name": "Coat",
            "garment_type": 35,
            "display_order": 3
        }
    },
    {
        "id": 17,
        "name": "coat_half_back",
        "description": "1/2 Back",
        "display_order": 4,
        "chinese_description": "半背宽",
        "garment_type": 33,
        "convunit": 1,
        "required": false,
        "active": 1,
        "measurement_group": {
            "id": 3,
            "name": "Coat",
            "garment_type": 35,
            "display_order": 3
        }
    },
    {
        "id": 18,
        "name": "coat_waist",
        "description": "Coat Waist",
        "display_order": 5,
        "chinese_description": "上衣腰围",
        "garment_type": 35,
        "convunit": 1,
        "required": false,
        "active": 1,
        "measurement_group": {
            "id": 3,
            "name": "Coat",
            "garment_type": 35,
            "display_order": 3
        }
    },
    {
        "id": 19,
        "name": "coat_half_girth",
        "description": "1/2 Girth",
        "display_order": 6,
        "chinese_description": "中腰",
        "garment_type": 33,
        "convunit": 1,
        "required": true,
        "active": 1,
        "measurement_group": {
            "id": 3,
            "name": "Coat",
            "garment_type": 35,
            "display_order": 3
        }
    },
    ...
]
```

Returns an array of measurements.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/measurements`

### Query Parameters

| Parameter       | Default | Description                                                       |
| --------------- | ------- | ----------------------------------------------------------------- |
| active          | N/A     | If set, returns only only active or inactive measurements.             |
| q               | N/A     | If set, return all fuzzy matched measurement names and descriptions. |
| measurement_group_id | N/A     | If set, will return any measurements in a specific measurement group. |
| garment_type    | N/A     | If set, returns all measurements that match a garment bitmask (E.g., 2 for Vests). |

### Other

- Permissions: N/A
- Pagination: Yes

### Example queries

#### Wildcard Search

Ex. Search for measurements mentioning "girth"

`GET https://api.trinity-apparel.com/v1/measurement?q=girth`

#### Search by Garment Type

Ex. List pant measurements

`GET https://api.trinity-apparel.com/v1/measurements?garment_type=4`


## Get a Specific Measurement

```shell
curl "https://api.trinity-apparel.com/v1/measurements/229"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
    "id": 6,
    "name": "coat_fit",
    "description": "Coat Fit",
    "display_order": 4,
    "chinese_description": "成衣效果",
    "garment_type": 33,
    "convunit": 0,
    "required": true,
    "active": 1,
    "measurement_group": {
        "id": 2,
        "name": "Body Description",
        "garment_type": 239,
        "display_order": 2
    },
    "measurement_values": [
        {
            "id": 84,
            "value": "regular",
            "description": "Regular",
            "display_order": 1
        },
        {
            "id": 85,
            "value": "trim",
            "description": "Trim",
            "display_order": 2
        },
        {
            "id": 86,
            "value": "easy",
            "description": "Easy",
            "display_order": 3
        }
    ]
}
```

Returns details on a specific measurement, including the measurement group and any defined measurement values.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/measurements/:id`

### Query Parameters

| Parameter | Default | Description                               |
| --------- | ------- | ----------------------------------------- |
| id.       | N/A     | The specific id you want to see           |

### Other

- Permissions: N/A
- Pagination: N/A


## Get All Measurement Values

```shell
curl "https://api.trinity-apparel.com/v1/measurement_values"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    ...,
    {
        "id": 184,
        "value": "normal",
        "description": "Normal",
        "display_order": 1,
        "measurement": {
            "id": 123,
            "name": "posture",
            "description": "Posture",
            "display_order": 12
        }
    },
    {
        "id": 185,
        "value": "erect",
        "description": "Erect",
        "display_order": 2,
        "measurement": {
            "id": 123,
            "name": "posture",
            "description": "Posture",
            "display_order": 12
        }
    },
    {
        "id": 186,
        "value": "stooping",
        "description": "Stooping",
        "display_order": 3,
        "measurement": {
            "id": 123,
            "name": "posture",
            "description": "Posture",
            "display_order": 12
        }
    },
    {
        "id": 187,
        "value": "head_forward",
        "description": "Head Forward",
        "display_order": 4,
        "measurement": {
            "id": 123,
            "name": "posture",
            "description": "Posture",
            "display_order": 12
        }
    },
    {
        "id": 188,
        "value": "erect_slightly",
        "description": "Erect - Slightly (1/8\")",
        "display_order": 1,
        "measurement": {
            "id": 124,
            "name": "posture_amt",
            "description": "Posture Amount",
            "display_order": 13
        }
    },
    {
        "id": 189,
        "value": "erect_moderately",
        "description": "Erect - Moderately (3/8\")",
        "display_order": 2,
        "measurement": {
            "id": 124,
            "name": "posture_amt",
            "description": "Posture Amount",
            "display_order": 13
        }
    },
    {
        "id": 190,
        "value": "erect_maximum",
        "description": "Erect - Maximum (5/8\")",
        "display_order": 3,
        "measurement": {
            "id": 124,
            "name": "posture_amt",
            "description": "Posture Amount",
            "display_order": 13
        }
    },
    ...
]
```

Returns an array of measurement values.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/measurement_values`

### Query Parameters

| Parameter       | Default | Description                                                           |
| --------------- | ------- | --------------------------------------------------------------------- |
| active          | N/A     | If set, returns only only active or inactive measurements.            |
| q               | N/A     | If set, return all fuzzy matched measurement names and descriptions.  |
| measurement_id  | N/A     | If set, will return any measurement values in a specific measurement  |
| garment_type    | N/A     | If set, returns all measurement values that match a garment bitmask (E.g., 2 for Vests). |

### Other

- Permissions: N/A
- Pagination: Yes

### Example queries

#### Wildcard Search

Ex. Search for measurement values mentioning "easy"

`GET https://api.trinity-apparel.com/v1/measurement_values?q=easy`

#### Search by Garment Type

Ex. List shirt measurement values

`GET https://api.trinity-apparel.com/v1/measurement_values?garment_type=8`

#### Search by Measurement

Ex. List all values for Perkins Posturegar

`GET https://api.trinity-apparel.com/v1/measurement_values?measurement_id=8`

#### Wildcard Search and Garment Type 

Ex. List jacket measurement values that mentioning "stooping"

`GET https://api.trinity-apparel.com/v1/measurement_values?garment_type=1&q=stooping`


## Get a Specific Measurement Value

```shell
curl "https://api.trinity-apparel.com/v1/measurement_values/10"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
    "id": 10,
    "value": "extremely_sloping",
    "description": "Extremely Sloping",
    "display_order": 4,
    "measurement": {
        "id": 46,
        "name": "shirt_shoulder_desc_r",
        "description": "Shoulder Description (R)",
        "display_order": 2
    }
}
```

Returns details on a specific measurement value, which includes the parent measurement.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/measurement_values/:id`

### Query Parameters

| Parameter | Default | Description                               |
| --------- | ------- | ----------------------------------------- |
| id.       | N/A     | The specific id you want to see           |

### Other

- Permissions: N/A
- Pagination: N/A