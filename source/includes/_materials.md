# Materials API

## Material Resources

The current materials are Buttons, Felts, Labels, Suedes, and Threads.  Each material has it's own endpoint, but they all work in a nearly identical way and provide the same routes and parameter's.  The only exception is Threads as it also returns and can be filtered on a code.

### Buttons, Felts, Labels, Suedes

```json
# Standard Object - Used in a resource collection
{
  "value": "KYKW023_Tan",
  "description": "2-10 Tan Marbled Premium",
  "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-10_Tan_Marbled_Premium?wid=100",
  "rgb": "107,96,72",
  "display_order": 31,
  "active": 1
}
```

Standard Attributes

| Attribute                               | Description                                                    |
| --------------------------------------- | -------------------------------------------------------------- |
| value <br> <span>string</span>          | Unique identifier for the material.                            |
| description <br> <span>string</span>    | Human readable description of the material.                    |
| image <br> <span>string</span>          | The url for an image of the material.                          |
| rgb <br> <span>string</span>            | The RGB code for the primary color of the material.            |
| display_order <br> <span>integer</span> | The order that the material is displayed in Workflow.          |
| active <br> <span>boolean</span>        | Inactive materials are removed from search results by default. |

### Material Threads

```json
# Standard Object - Used in a resource collection
{
  "value": "black",
  "code": "C9770",
  "description": "Black",
  "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Colcolor=36,36,36&fmt=png-alpha",
  "rgb": "36,36,36",
  "display_order": 4,
  "active": 1
}
```

Standard Attributes

| Attribute                               | Description                                                  |
| --------------------------------------- | ------------------------------------------------------------ |
| value <br> <span>string</span>          | Unique identifier for the thread.                            |
| code <br> <span>string</span>           | A five digit code used for Milanese Lapels.                  |
| description <br> <span>string</span>    | Human readable description of the thread.                    |
| image <br> <span>string</span>          | The url for an image of the thread.                          |
| rgb <br> <span>string</span>            | The RGB code for the primary color of the thread.            |
| display_order <br> <span>integer</span> | The order that the thread is displayed in Workflow.          |
| active <br> <span>boolean</span>        | Inactive threads are removed from search results by default. |

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

## Get a Specific Button

```shell
curl "https://api.trinity-apparel.com/v1/buttons/KYKW022_Black"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
  "value": "KYKW022_Black",
  "description": "2-04 Black Marbled Premium",
  "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-04_Black_Marbled_Premium?wid=100",
  "rgb": "43,43,43",
  "display_order": 30,
  "active": 1
}
```

Returns details on a specific button.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/buttons/:value`

### Query Parameters

| Parameter | Default | Description                               |
| --------- | ------- | ----------------------------------------- |
| value     | N/A     | The specific button value you want to see |

### Other

- Permissions: All
- Pagination: N/A

## Get All Felts

```shell
curl "https://api.trinity-apparel.com/v1/felts"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "value": "KYFLD-90642-1_ivory",
        "description": "6-01 Ivory",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-01_Ivory?&hei=100",
        "rgb": "239,232,225",
        "display_order": 1,
        "active": true
    },
    {
        "value": "KYFLD-90642-11_red",
        "description": "6-19 Red",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-19_Red?&hei=100",
        "rgb": "159,17,31",
        "display_order": 19,
        "active": true
    },
    {
        "value": "KYFLD-90642-13_emerald_green",
        "description": "6-44 Emerald Green",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-44_Emerald?&hei=100",
        "rgb": "79,73,41",
        "display_order": 44,
        "active": true
    },
    {
        "value": "KYFLD-90985-6_purple",
        "description": "6-15 Purple",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-15_Purple?&hei=100",
        "rgb": "60,40,53",
        "display_order": 15,
        "active": true
    },
    {
        "value": "FLD-0614_navy",
        "description": "6-07 Navy",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-07_Navy?&hei=100",
        "rgb": "39,39,49",
        "display_order": 7,
        "active": true
    },
    {
        "value": "KYFLD-90985-8_maroon",
        "description": "6-17 Maroon",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-17_Maroon?&hei=100",
        "rgb": "80,28,31",
        "display_order": 17,
        "active": true
    },
    {
        "value": "KYFLD-90985-11_royal_blue",
        "description": "6-09 Royal Blue",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-09_Royal_Blue?&hei=100",
        "rgb": "39,92,174",
        "display_order": 9,
        "active": true
    },
    {
        "value": "KYFLD-90985-16_forest_green",
        "description": "6-46 Forest Green",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-46_Forest_Green?&hei=100",
        "rgb": "62,79,59",
        "display_order": 46,
        "active": true
    },
    {
        "value": "FLD-0634_black",
        "description": "6-05 Black",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-05_Black?&hei=100",
        "rgb": "30,30,30",
        "display_order": 5,
        "active": true
    },
    {
        "value": "FLD-0626_charcoal",
        "description": "6-04 Charcoal",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-04_Charcoal?&hei=100",
        "rgb": "56,52,52",
        "display_order": 4,
        "active": true
    },
    {
        "value": "FLD-0640_midnight_blue",
        "description": "6-06 Midnight Blue",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-06_Midnight_Blue?&hei=100",
        "rgb": "36,43,64",
        "display_order": 6,
        "active": true
    },
    {
        "value": "FLD-0625_moss_green",
        "description": "6-43 Moss Green",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-43_Moss?&hei=100",
        "rgb": "97,83,72",
        "display_order": 43,
        "active": true
    },
    {
        "value": "FLD-0695_vicuna",
        "description": "6-26 Vicuna",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-26_Vicuna?&hei=100",
        "rgb": "188,127,76",
        "display_order": 26,
        "active": true
    },
    {
        "value": "FLD-0620_dark_brown",
        "description": "6-28 Dark Brown",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-28_Dark_Brown?&hei=100",
        "rgb": "81,56,45",
        "display_order": 28,
        "active": true
    },
    {
        "value": "FLD-0630_light_gray",
        "description": "6-03 Light Gray",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-03_Light_Gray?&hei=100",
        "rgb": "141,136,133",
        "display_order": 3,
        "active": true
    },
    {
        "value": "FLD-F900-38_teal_blue",
        "description": "6-39 Teal Blue",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-39_Teal_Blue?&hei=100",
        "rgb": "87,160,149",
        "display_order": 39,
        "active": true
    },
    {
        "value": "FLD-F900-46_lavender",
        "description": "6-14 Lavender",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-14_Lavender?&hei=100",
        "rgb": "148,106,143",
        "display_order": 14,
        "active": true
    },
    {
        "value": "FLD-F900-F8_pink",
        "description": "6-21 Pink",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-21_Pink?&hei=100",
        "rgb": "254,148,163",
        "display_order": 21,
        "active": true
    },
    {
        "value": "FLD-F900-27_olive",
        "description": "6-45 Olive",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-45_Olive?&hei=100",
        "rgb": "67,68,49",
        "display_order": 45,
        "active": true
    },
    {
        "value": "FLD-F900-26_ecru",
        "description": "6-23 Ecru",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-23_Ecru?&hei=100",
        "rgb": "216,202,185",
        "display_order": 23,
        "active": true
    },
    {
        "value": "FLD-F900-17_celery",
        "description": "6-41 Celery",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-41_Celery?&hei=100",
        "rgb": "155,139,110",
        "display_order": 41,
        "active": true
    },
    {
        "value": "FLD-F900-20_sage",
        "description": "6-42 Sage",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-42_Sage?&hei=100",
        "rgb": "132,108,77",
        "display_order": 42,
        "active": true
    },
    {
        "value": "NB101_camel",
        "description": "6-25 Camel",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-25_Camel?&hei=100",
        "rgb": "163,124,87",
        "display_order": 25,
        "active": true
    },
    {
        "value": "NB112_cranberry",
        "description": "6-18 Cranberry",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-18_Cranberry?&hei=100",
        "rgb": "97,30,36",
        "display_order": 18,
        "active": true
    },
    {
        "value": "NB010_french_blue",
        "description": "6-08 French Blue",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-08_French_Blue?&hei=100",
        "rgb": "23,83,130",
        "display_order": 8,
        "active": true
    }
]
```

Returns an array of active felts.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/felts`

### Query Parameters

| Parameter       | Default | Description                                                     |
| --------------- | ------- | --------------------------------------------------------------- |
| show_archived   | false   | If set to true, the result will also include inactive felts.    |
| description     | N/A     | If set, will return any felts with exact matching descriptions. |
| q               | N/A     | If set, return all fuzzy matched descriptions.                  |
| option_value_id | N/A     | If set, returns all valid felts for that option value.          |

### Other

- Permissions: All
- Pagination: Yes

### Querying by multiple felt descriptions

In order to query for multiple felts, you will pass in multiple params with the format like below:

`GET https://api.trinity-apparel.com/v1/felts?description[]=6-01 Ivory&description[]=6-07 Navy&description[]=6-17 Maroon`

## Get a Specific Felt

```shell
curl "https://api.trinity-apparel.com/v1/felts/KYFLD-90985-6_purple"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
  "value": "KYFLD-90985-6_purple",
  "description": "6-15 Purple",
  "image": "http://s7d4.scene7.com/is/image/trinityapparel/6-15_Purple?&hei=100",
  "rgb": "60,40,53",
  "display_order": 15,
  "active": true
}
```

Returns details on a specific felt.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/felts/:value`

### Query Parameters

| Parameter | Default | Description                             |
| --------- | ------- | --------------------------------------- |
| value     | N/A     | The specific felt value you want to see |

### Other

- Permissions: All
- Pagination: N/A