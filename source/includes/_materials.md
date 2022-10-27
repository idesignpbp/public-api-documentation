# Materials API

## Material Resources

The current materials are Buttons, Felts, Labels, Piping, Suedes, Threads, Trouser Trim, and Zippers. Each material has its own endpoint, but they all work in a nearly identical way and provide the same routes and parameters. The only exception is Threads, which also returns and can be filtered on a code.

### Buttons, Felts, Labels, Piping, Suedes, Threads, Trouser Trim, Zippers

```json
# Standard Object - Used in a resource collection
{
  "value": "KYKW023_Tan",
  "description": "2-10 Tan Marbled Premium",
  "code": "2-10",
  "title": "Tan Marbled",
  "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-10_Tan_Marbled_Premium?hei=200",
  "rgb": "107,96,72",
  "display_order": 31,
  "active": true
}
```

Standard Attributes

| Attribute                               | Description                                                              |
| --------------------------------------- | ------------------------------------------------------------------------ |
| value <br> <span>string</span>          | Unique identifier for the material.                                      |
| description <br> <span>string</span>    | Human readable description of the material.                              |
| code <br> <span>string</span>           | Used internally to determine which button can be used on which garments. |
| title <br> <span>string</span>          | The description with the code removed.                                   |
| image <br> <span>string</span>          | The url for an image of the material.                                    |
| rgb <br> <span>string</span>            | The RGB code for the primary color of the material.                      |
| display_order <br> <span>integer</span> | The order that the material is displayed in Workflow.                    |
| active <br> <span>boolean</span>        | Inactive materials are removed from search results by default.           |

### Threads

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
    "code": "2-10",
    "title": "Tan Marbled",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-10_Tan_Marbled_Premium?hei=200",
    "rgb": "107,96,72",
    "display_order": 31,
    "active": true
  },
  {
    "value": "KYKW024_Cinnamon",
    "description": "2-11 Cinnamon Marbled Premium",
    "code": "2-11",
    "title": "Cinnamon Marbled",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-11_Cinnamon_Marbled_Premium?hei=200",
    "rgb": "115,76,62",
    "display_order": 32,
    "active": true
  },
  {
    "value": "KYKW025_Taupe",
    "description": "2-12 Taupe Marbled Premium",
    "code": "2-12",
    "title": "Taupe Marbled",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-12_Taupe_Marbled_Premium?hei=200",
    "rgb": "99,93,69",
    "display_order": 33,
    "active": true
  },
  {
    "value": "KYKW026_Grey",
    "description": "2-02 Grey Marbled Premium",
    "code": "2-02",
    "title": "Grey Marbled",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-02_Grey_Marbled_Premium?hei=200",
    "rgb": "79,79,76",
    "display_order": 34,
    "active": true
  },
  {
    "value": "KYKW027_Dark_Brown",
    "description": "2-13 Dark Brown Marbled Premium",
    "code": "2-13",
    "title": "Dark Brown Marbled",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-13_Dark_Brown_Marbled_Premium?hei=200",
    "rgb": "46,36,23",
    "display_order": 35,
    "active": true
  },
  {
    "value": "KYKW028_Charcoal",
    "description": "2-03 Charcoal Marbled Premium",
    "code": "2-03",
    "title": "Charcoal Marbled",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-03_Charcoal_Marbled_Premium?hei=200",
    "rgb": "50,50,50",
    "display_order": 36,
    "active": true
  },
  {
    "value": "KYKW022_Black",
    "description": "2-04 Black Marbled Premium",
    "code": "2-04",
    "title": "Black Marbled",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-04_Black_Marbled_Premium?hei=200",
    "rgb": "43,43,43",
    "display_order": 30,
    "active": true
  },
  {
    "value": "KW017_Shield",
    "description": "2-23 Shield Premium",
    "code": "2-23",
    "title": "Shield",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-23_Shield_Premium?hei=200",
    "rgb": "43,43,43",
    "display_order": 28,
    "active": true
  },
  {
    "value": "KW018_Skull",
    "description": "2-24 Skull Premium",
    "code": "2-24",
    "title": "Skull",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-24_Skull_Premium?hei=200",
    "rgb": "157,157,157",
    "display_order": 29,
    "active": true
  },
  {
    "value": "KB002_White_MOP",
    "description": "1-31 White Mother of Pearl",
    "code": "1-31",
    "title": "White Mother of Pearl",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-31_White_Mother_of_Pearl?hei=200",
    "rgb": "233,235,226",
    "display_order": 17,
    "active": true
  },
  {
    "value": "KB001_Smoke_MOP",
    "description": "1-32 Smoke Mother of Pearl",
    "code": "1-32",
    "title": "Smoke Mother of Pearl",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-32_Smoke_Mother_of_Pearl?hei=200",
    "rgb": "46,58,73",
    "display_order": 18,
    "active": true
  },
  {
    "value": "KG034_Dark_Olive",
    "description": "1-26 Dark Olive",
    "code": "1-26",
    "title": "Dark Olive",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-26_Dark_Olive?hei=200",
    "rgb": "49,49,27",
    "display_order": 19,
    "active": true
  },
  {
    "value": "KG036_Navy",
    "description": "1-08 Navy",
    "code": "1-08",
    "title": "Navy",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-08_Navy?hei=200",
    "rgb": "37,37,49",
    "display_order": 5,
    "active": true
  },
  {
    "value": "KG038_Dark_Taupe",
    "description": "1-25 Dark Taupe",
    "code": "1-25",
    "title": "Dark Taupe",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-25_Dark_Taupe?hei=200",
    "rgb": "69,45,42",
    "display_order": 6,
    "active": true
  },
  {
    "value": "KG051_Ivory",
    "description": "1-18 Ivory",
    "code": "1-18",
    "title": "Ivory",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-18_Ivory?hei=200",
    "rgb": "254,235,179",
    "display_order": 8,
    "active": true
  },
  {
    "value": "KG052_Coffee",
    "description": "1-22 Coffee",
    "code": "1-22",
    "title": "Coffee",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-22_Coffee?hei=200",
    "rgb": "107,81,45",
    "display_order": 9,
    "active": true
  },
  {
    "value": "KG039_Charcoal_Grey",
    "description": "1-05 Charcoal Gray",
    "code": "1-05",
    "title": "Charcoal Gray",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-05_Charcoal_Gray?hei=200",
    "rgb": "77,75,75",
    "display_order": 4,
    "active": true
  },
  {
    "value": "KG041_Sand",
    "description": "1-19 Sand",
    "code": "1-19",
    "title": "Sand",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-19_Sand?hei=200",
    "rgb": "185,160,120",
    "display_order": 7,
    "active": true
  },
  {
    "value": "KG056_Caramel",
    "description": "1-20 Caramel",
    "code": "1-20",
    "title": "Caramel",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-20_Caramel?hei=200",
    "rgb": "133,109,72",
    "display_order": 10,
    "active": true
  },
  {
    "value": "KG062_Tan",
    "description": "1-21 Tan",
    "code": "1-21",
    "title": "Tan",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-21_Tan?hei=200",
    "rgb": "130,86,31",
    "display_order": 11,
    "active": true
  },
  {
    "value": "KG064_Medium_Brown",
    "description": "1-23 Medium Brown",
    "code": "1-23",
    "title": "Medium Brown",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-23_Medium_Brown?hei=200",
    "rgb": "85,60,36",
    "display_order": 12,
    "active": true
  },
  {
    "value": "KG069_Dark_Brown",
    "description": "1-24 Dark Brown",
    "code": "1-24",
    "title": "Dark Brown",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-24_Dark_Brown?hei=200",
    "rgb": "50,34,18",
    "display_order": 13,
    "active": true
  },
  {
    "value": "KG019_Black",
    "description": "1-06 Black",
    "code": "1-06",
    "title": "Black",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-06_Black?hei=200",
    "rgb": "43,43,43",
    "display_order": 3,
    "active": true
  },
  {
    "value": "KNJ011_Dark_Brown",
    "description": "1-30 Dark Brown Horn",
    "code": "1-30",
    "title": "Dark Brown Horn",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-30_Dark_Brown_Horn?hei=200",
    "rgb": "33,35,32",
    "display_order": 14,
    "active": true
  },
  {
    "value": "KNJ012_Medium_Brown",
    "description": "1-28 Medium Brown Horn",
    "code": "1-28",
    "title": "Medium Brown Horn",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/1-28_Medium_Brown_Horn?hei=200",
    "rgb": "72,52,31",
    "display_order": 15,
    "active": true
  }
]
```

Returns an array of active buttons.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/buttons`

### Query Parameters

| Parameter       | Default | Description                                                                        |
| --------------- | ------- | ---------------------------------------------------------------------------------- |
| show_archived   | false   | If set to true, the result will also include inactive buttons.                     |
| description     | N/A     | If set, will return any buttons with exact matching descriptions.                  |
| q               | N/A     | If set, return all fuzzy matched descriptions.                                     |
| option_value_id | N/A     | If set, returns all valid buttons for that option value.                           |
| garment_type    | N/A     | If set, returns all valid buttons for those [garment_type bitmask](#garment-types) |

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
  "code": "2-04",
  "title": "Black Marbled",
  "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-04_Black_Marbled_Premium?hei=200",
  "rgb": "43,43,43",
  "display_order": 30,
  "active": true
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

## Get All Labels

```shell
curl "https://api.trinity-apparel.com/v1/labels"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
  {
    "value": "ivory_label",
    "description": "Ivory Label",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/ivory_label?wid=300",
    "rgb": null,
    "display_order": 0,
    "active": 1
  },
  {
    "value": "purple_label",
    "description": "Purple Label",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/purple_label?wid=300",
    "rgb": null,
    "display_order": 1,
    "active": 1
  },
  {
    "value": "green_label",
    "description": "Green Label",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/green_label?wid=300",
    "rgb": null,
    "display_order": 2,
    "active": 1
  },
  {
    "value": "tan_label",
    "description": "Tan Label",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/tan_label?wid=300",
    "rgb": null,
    "display_order": 3,
    "active": 1
  },
  {
    "value": "maroon_label",
    "description": "Maroon Label",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/maroon_label?wid=300",
    "rgb": null,
    "display_order": 4,
    "active": 1
  },
  {
    "value": "blue_label",
    "description": "Blue Label",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/blue_label?wid=300",
    "rgb": null,
    "display_order": 5,
    "active": 1
  },
  {
    "value": "sky_blue_label",
    "description": "Sky Blue Label",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/sky_blue_label?wid=300",
    "rgb": null,
    "display_order": 6,
    "active": 1
  },
  {
    "value": "orange_label",
    "description": "Orange Label",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/orange_label?wid=300",
    "rgb": null,
    "display_order": 7,
    "active": 1
  },
  {
    "value": "red_label",
    "description": "Red Label",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/red_label?wid=300",
    "rgb": null,
    "display_order": 8,
    "active": 1
  },
  {
    "value": "label",
    "description": "Black Label",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/black_label?wid=300",
    "rgb": null,
    "display_order": 9,
    "active": 1
  },
  {
    "value": "direct_embroider_lining",
    "description": "Embroider Directly on Garment Lining",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/Embroidery_Lining?wid=300",
    "rgb": null,
    "display_order": 10,
    "active": 1
  },
  {
    "value": "direct_embroider_undercollar",
    "description": "Embroidery Directly on Undercollar Felt/Microsuede",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/Embroidery_Undercollar?wid=300",
    "rgb": null,
    "display_order": 11,
    "active": 1
  },
  {
    "value": "no",
    "description": "No",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/no_label?wid=300",
    "rgb": null,
    "display_order": 12,
    "active": 1
  },
  {
    "value": "yellow_label",
    "description": "Yellow Label",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/yellow_label?wid=300",
    "rgb": null,
    "display_order": 13,
    "active": 1
  },
  {
    "value": "light_gray_label",
    "description": "Light Gray Label",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/light_grey_label?wid=300",
    "rgb": null,
    "display_order": 14,
    "active": 1
  }
]
```

Returns an array of active labels.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/labels`

### Query Parameters

| Parameter       | Default | Description                                                      |
| --------------- | ------- | ---------------------------------------------------------------- |
| show_archived   | false   | If set to true, the result will also include inactive labels.    |
| description     | N/A     | If set, will return any labels with exact matching descriptions. |
| q               | N/A     | If set, return all fuzzy matched descriptions.                   |
| option_value_id | N/A     | If set, returns all valid labels for that option value.          |

### Other

- Permissions: All
- Pagination: Yes

### Querying by multiple label descriptions

In order to query for multiple labels, you will pass in multiple params with the format like below:

`GET https://api.trinity-apparel.com/v1/labels?description[]=Ivory Label&description[]=Maroon Label&description[]=Sky Blue Label`

## Get a Specific Label

```shell
curl "https://api.trinity-apparel.com/v1/labels/orange_label"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
  "value": "orange_label",
  "description": "Orange Label",
  "image": "http://s7d4.scene7.com/is/image/trinityapparel/orange_label?wid=300",
  "rgb": null,
  "display_order": 7,
  "active": 1
}
```

Returns details on a specific label.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/labels/:value`

### Query Parameters

| Parameter | Default | Description                              |
| --------- | ------- | ---------------------------------------- |
| value     | N/A     | The specific label value you want to see |

### Other

- Permissions: All
- Pagination: N/A

## Get All Suedes

```shell
curl "https://api.trinity-apparel.com/v1/suedes"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
  {
    "value": "MS-219183_silver",
    "description": "7-02 Silver",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-02_Silver?&hei=100",
    "rgb": "212,212,212",
    "display_order": 2,
    "active": true
  },
  {
    "value": "MS-219184_gray",
    "description": "7-03 Gray",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-03_Gray?&hei=100",
    "rgb": "111,98,110",
    "display_order": 3,
    "active": true
  },
  {
    "value": "MS-219185_charcoal",
    "description": "7-04 Charcoal",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-04_Charcoal?&hei=100",
    "rgb": "85,83,83",
    "display_order": 4,
    "active": true
  },
  {
    "value": "MS-219186_black",
    "description": "7-05 Black",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-05_Black?&hei=100",
    "rgb": "0,0,0",
    "display_order": 5,
    "active": true
  },
  {
    "value": "MS-219187_lt__blue",
    "description": "7-08 Blue",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-08_Blue?&hei=100",
    "rgb": "37,53,97",
    "display_order": 8,
    "active": true
  },
  {
    "value": "MS-219188_blue",
    "description": "7-07 Navy",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-07_Navy?&hei=100",
    "rgb": "56,57,73",
    "display_order": 7,
    "active": true
  },
  {
    "value": "MS-219189_navy",
    "description": "7-06 Midnight Blue",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-06_Midnight_Blue?&hei=100",
    "rgb": "41,37,49",
    "display_order": 6,
    "active": true
  },
  {
    "value": "MS-219190_olive",
    "description": "7-39 Olive",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-39_Olive?&hei=100",
    "rgb": "99,94,76",
    "display_order": 39,
    "active": true
  },
  {
    "value": "MS-219191_camel",
    "description": "7-22 Sand",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-22_Sand?&hei=100",
    "rgb": "198,173,143",
    "display_order": 22,
    "active": true
  },
  {
    "value": "MS-219192_brown",
    "description": "7-25 Mocha",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-25_Mocha?&hei=100",
    "rgb": "106,69,39",
    "display_order": 25,
    "active": true
  },
  {
    "value": "MS-219193_chocolate",
    "description": "7-26 Dark Brown",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-26_Dark_Brown?&hei=100",
    "rgb": "56,43,32",
    "display_order": 26,
    "active": true
  },
  {
    "value": "MS-219194_rust",
    "description": "7-28 Orange",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-28_Orange?&hei=100",
    "rgb": "195,82,49",
    "display_order": 28,
    "active": true
  },
  {
    "value": "MS-219195_mahogany",
    "description": "7-27 Rust",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-27_Rust?&hei=100",
    "rgb": "135,55,38",
    "display_order": 27,
    "active": true
  },
  {
    "value": "MS-219196_burgundy",
    "description": "7-16 Burgundy",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-16_Burgundy?&hei=100",
    "rgb": "112,31,38",
    "display_order": 16,
    "active": true
  },
  {
    "value": "MS-219197_maroon",
    "description": "7-15 Maroon",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-15_Maroon?&hei=100",
    "rgb": "89,39,54",
    "display_order": 15,
    "active": true
  },
  {
    "value": "MS-219198_purple",
    "description": "7-14 Purple",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-14_Purple?&hei=100",
    "rgb": "92,59,87",
    "display_order": 14,
    "active": true
  },
  {
    "value": "MS-219199_lavender",
    "description": "7-13 Lavender",
    "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-13_Lavender?&hei=100",
    "rgb": "197,179,223",
    "display_order": 13,
    "active": true
  }
]
```

Returns an array of active suedes.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/suedes`

### Query Parameters

| Parameter       | Default | Description                                                      |
| --------------- | ------- | ---------------------------------------------------------------- |
| show_archived   | false   | If set to true, the result will also include inactive suedes.    |
| description     | N/A     | If set, will return any suedes with exact matching descriptions. |
| q               | N/A     | If set, return all fuzzy matched descriptions.                   |
| option_value_id | N/A     | If set, returns all valid suedes for that option value.          |

### Other

- Permissions: All
- Pagination: Yes

### Querying by multiple suede descriptions

In order to query for multiple suedes, you will pass in multiple params with the format like below:

`GET https://api.trinity-apparel.com/v1/suedes?description[]=7-03 Gray&description[]=7-05 Black&description[]=7-06 Midnight Blue`

## Get a Specific Suede

```shell
curl "https://api.trinity-apparel.com/v1/suedes/MS-219187_lt__blue"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
  "value": "MS-219187_lt__blue",
  "description": "7-08 Blue",
  "image": "http://s7d4.scene7.com/is/image/trinityapparel/7-08_Blue?&hei=100",
  "rgb": "37,53,97",
  "display_order": 8,
  "active": true
}
```

Returns details on a specific suede.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/suedes/:value`

### Query Parameters

| Parameter | Default | Description                              |
| --------- | ------- | ---------------------------------------- |
| value     | N/A     | The specific suede value you want to see |

### Other

- Permissions: All
- Pagination: N/A

## Get All Threads

```shell
curl "https://api.trinity-apparel.com/v1/material_theads"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
  {
    "value": "black",
    "code": "C9770",
    "description": "Black",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=36,36,36&fmt=png-alpha",
    "rgb": "36,36,36",
    "display_order": 4,
    "active": 1
  },
  {
    "value": "navy",
    "code": "C7930",
    "description": "Navy",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=28,33,50&fmt=png-alpha",
    "rgb": "28,33,50",
    "display_order": 8,
    "active": 1
  },
  {
    "value": "ivory",
    "code": "C2740",
    "description": "Ivory",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=245,247,237&fmt=png-alpha",
    "rgb": "245,247,237",
    "display_order": 21,
    "active": 1
  },
  {
    "value": "light_gray",
    "code": "C9631",
    "description": "Light Gray",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=172,167,172&fmt=png-alpha",
    "rgb": "172,167,172",
    "display_order": 7,
    "active": 1
  },
  {
    "value": "medium_gray",
    "code": "C9623",
    "description": "Medium Gray",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=153,156,158&fmt=png-alpha",
    "rgb": "153,156,158",
    "display_order": 6,
    "active": 1
  },
  {
    "value": "dark_gray",
    "code": "C9949",
    "description": "Dark Gray",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=110,111,112&fmt=png-alpha",
    "rgb": "110,111,112",
    "display_order": 5,
    "active": 1
  },
  {
    "value": "trinity_blue",
    "code": "C7305",
    "description": "Trinity Blue",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=40,81,147&fmt=png-alpha",
    "rgb": "40,81,147",
    "display_order": 11,
    "active": 1
  },
  {
    "value": "blue",
    "code": "C7201",
    "description": "Blue",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=139,187,226&fmt=png-alpha",
    "rgb": "139,187,226",
    "display_order": 33,
    "active": 1
  },
  {
    "value": "light_blue",
    "code": "C7279",
    "description": "Light Blue",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=162,196,204&fmt=png-alpha",
    "rgb": "162,196,204",
    "display_order": 10,
    "active": 1
  },
  {
    "value": "dark_brown",
    "code": "C8989",
    "description": "Dark Brown",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=94,70,61&fmt=png-alpha",
    "rgb": "94,70,61",
    "display_order": 14,
    "active": 1
  },
  {
    "value": "medium_brown",
    "code": "C8587",
    "description": "Medium Brown",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=175,129,86&fmt=png-alpha",
    "rgb": "175,129,86",
    "display_order": 15,
    "active": 1
  },
  {
    "value": "light_brown",
    "code": "C8501",
    "description": "Light Brown",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=214,176,137&fmt=png-alpha",
    "rgb": "214,176,137",
    "display_order": 18,
    "active": 1
  },
  {
    "value": "khaki",
    "code": "C2376",
    "description": "Khaki",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=237,200,147&fmt=png-alpha",
    "rgb": "237,200,147",
    "display_order": 13,
    "active": 1
  },
  {
    "value": "tan",
    "code": "C9313",
    "description": "Tan",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=209,190,170&fmt=png-alpha",
    "rgb": "209,190,170",
    "display_order": 12,
    "active": 1
  },
  {
    "value": "gold",
    "code": "C1257",
    "description": "Gold",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=253,216,121&fmt=png-alpha",
    "rgb": "253,216,121",
    "display_order": 25,
    "active": 1
  },
  {
    "value": "medium_olive",
    "code": "C5744",
    "description": "Medium Olive",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=131,130,52&fmt=png-alpha",
    "rgb": "131,130,52",
    "display_order": 12,
    "active": 1
  },
  {
    "value": "orange",
    "code": "C2427",
    "description": "Orange",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=255,137,38&fmt=png-alpha",
    "rgb": "255,137,38",
    "display_order": 0,
    "active": 1
  },
  {
    "value": "red",
    "code": "C3853",
    "description": "Red",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=182,33,28&fmt=png-alpha",
    "rgb": "182,33,28",
    "display_order": 24,
    "active": 1
  },
  {
    "value": "burgundy",
    "code": "C3993",
    "description": "Burgundy",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=122,40,41&fmt=png-alpha",
    "rgb": "122,40,41",
    "display_order": 0,
    "active": 1
  },
  {
    "value": "purple",
    "code": "C4983",
    "description": "Purple",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=69,43,81&fmt=png-alpha",
    "rgb": "69,43,81",
    "display_order": 0,
    "active": 1
  },
  {
    "value": "lavender",
    "code": "C4328",
    "description": "Lavender",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=133,109,155&fmt=png-alpha",
    "rgb": "133,109,155",
    "display_order": 19,
    "active": 1
  },
  {
    "value": "white",
    "code": "C1740",
    "description": "White",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=244,241,244&fmt=png-alpha",
    "rgb": "244,241,244",
    "display_order": 3,
    "active": 1
  },
  {
    "value": "charcoal",
    "code": "C9949",
    "description": "Charcoal",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=108,111,115&fmt=png-alpha",
    "rgb": "108,111,115",
    "display_order": 22,
    "active": 1
  },
  {
    "value": "silver",
    "code": "C9114",
    "description": "Silver",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=181,183,185&fmt=png-alpha",
    "rgb": "181,183,185",
    "display_order": 8,
    "active": 1
  },
  {
    "value": "beige",
    "code": "C1172",
    "description": "Beige",
    "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=233,232,128&fmt=png-alpha",
    "rgb": "233,232,128",
    "display_order": 30,
    "active": 1
  }
]
```

Returns an array of active threads.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/material_threads`

### Query Parameters

| Parameter       | Default | Description                                                       |
| --------------- | ------- | ----------------------------------------------------------------- |
| show_archived   | false   | If set to true, the result will also include inactive threads.    |
| code            | N/A     | If set, will return any threads with exact matching code.         |
| description     | N/A     | If set, will return any threads with exact matching descriptions. |
| q               | N/A     | If set, return all fuzzy matched descriptions.                    |
| option_value_id | N/A     | If set, returns all valid threads for that option value.          |

### Other

- Permissions: All
- Pagination: Yes

### Querying by multiple thread descriptions or codes

In order to query for multiple threads, you will pass in multiple params with the format like below:

`GET https://api.trinity-apparel.com/v1/material_threads?description[]=Black&description[]=Medium Gray&description[]=Trinity Blue`

OR

`GET https://api.trinity-apparel.com/v1/material_threads?code[]=C9770&code[]=C9949&code[]=C7305`

## Get a Specific Thread

```shell
curl "https://api.trinity-apparel.com/v1/material_threads/trinity_blue"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
  "value": "trinity_blue",
  "code": "C7305",
  "description": "Trinity Blue",
  "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Colorcolor=40,81,147&fmt=png-alpha",
  "rgb": "40,81,147",
  "display_order": 11,
  "active": 1
}
```

Returns details on a specific thread.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/material_threads/:value`

### Query Parameters

| Parameter | Default | Description                               |
| --------- | ------- | ----------------------------------------- |
| value     | N/A     | The specific thread value you want to see |

### Other

- Permissions: All
- Pagination: N/A

## Update Fabric Match

```shell
curl -X POST "https://api.trinity-apparel.com/v1/garments/:id/fabric_match"
  -H "Authorization Bearer: swaledale"
```

> The above command returns Garment Properties JSON structured like this:

```json
{
  "measurements": [
{
      "id": 2,
      "name": "height",
      "description": "Height",
      "value": 182.88,
      "last_modified": "2019-06-27 14:05:57 UTC",
      "garment_type": 7,
      "garment_types": [
        "csc",
        "cv",
        "ct"
      ],
      "units": "cm"
    },

    ...
  ],
  "options": [
{
      "option": {
        "id": 1,
        "name": "garment_label",
        "description": "Garment Label"
      },
      "option_value": {
        "id": 374,
        "value": "dealer_label",
        "description": "用客供商标"
      },
      "garment_type": 1,
      "garment_types": [
        "csc"
      ]
    },

    ...
  ],

  "materials": {
    "fabrics": [
      {
        "id": 73096,
        "name": "K4-3973096",
        "description": "Black Fancy Solid",
        "image": "https://s7d4.scene7.com/is/image/trinityapparel/K4-3973096",
        "options": [
          {
            "id": null,
            "name": "shell",
            "description": "Shell Fabric",
            "garment_type": 5,
            "garment_types": [
              "csc",
              "ct"
            ]
          }
        ],
        "usage": "shell",
        "trinity_number": "K4-3973096",
        "supplier_number": "C21125-01",
        "quantity": {
          "cad": {
            "width": null,
            "length": null,
            "is_cut": null
          },
          "received": {
            "width": null,
            "length": null,
            "notes": null
          },
          "repeated_pattern": {
            "width": null,
            "length": null,
            "type": null
          }
        }
      },
      ...
    ],
      ...
    "buttons": [
      {
        "id": 2,
        "name": "KYKW024_Cinnamon",
        "description": "2-11 Cinnamon Marbled Premium",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/2-11_Cinnamon_Marbled_Premium?wid=100",
        "options": [
          {
            "id": 21,
            "name": "button_color",
            "description": "Button Color/Type",
            "garment_type": 1,
            "garment_types": [
              "csc"
            ]
          },
          {
            "id": 244,
            "name": "button_color",
            "description": "Button Color/Type",
            "garment_type": 4,
            "garment_types": [
              "ct"
            ]
          },
          {
            "id": 290,
            "name": "button_color",
            "description": "Button Color/Type",
            "garment_type": 2,
            "garment_types": [
              "cv"
            ]
          },
          {
            "id": 507,
            "name": "materials_button_color",
            "description": "Button Color",
            "garment_type": 1,
            "garment_types": [
              "csc"
            ]
          },
          {
            "id": 512,
            "name": "materials_button_color",
            "description": "Button Color/Type",
            "garment_type": 2,
            "garment_types": [
              "cv"
            ]
          },
          {
            "id": 516,
            "name": "materials_button_color",
            "description": "Button Color/Type",
            "garment_type": 4,
            "garment_types": [
              "ct"
            ]
          }
        ],
        "quantity": {
          "32L": {
            "csc": 3
          },
          "24L": {
            "csc": 16,
            "cv": 8,
            "ct": 3
          }
        }
      }
    ],
    "threads": [
      {
        "id": 27,
        "name": "silver",
        "description": "Silver",
        "image": "http://s7d4.scene7.com/ir/render/trinityapparelrender/buttonhole?wid=112&obj=Buttonhole/Color&color=231,231,231&fmt=png-alpha",
        "options": [
          {
            "id": 225,
            "name": "pic_stitching_lining_edge",
            "description": "Pic Stitching - Lining Edge",
            "garment_type": 1,
            "garment_types": [
              "csc"
            ]
          },
          ...
        ]
      }
    ],
    "suedes": [],
    "labels": [
      {
        "id": 11,
        "name": "direct_embroider_lining",
        "description": "Embroider Directly on Garment Lining",
        "image": "http://s7d4.scene7.com/is/image/trinityapparel/Embroidery_Lining?wid=300",
        "options": [
          {
            "id": 84,
            "name": "customer_label",
            "description": "Coat Name Label",
            "garment_type": 1,
            "garment_types": [
              "csc"
            ]
          }
        ]
      },
      ...
    ],
    "pocket_bags": [
      {
        "id": null,
        "name": "front_pocket_l",
        "description": "Default Front Left Pocket Bag",
        "image": null,
        "options": [
          {
            "id": null,
            "name": "front_pockets",
            "description": "front_pockets",
            "garment_type": 4,
            "garment_types": [
              "ct"
            ]
          }
        ],
        "quantity": {
          "length": 14.57,
          "width": 7.87
        }
      },
      ...
    ],
    "dealer_labels": [
      {
        "id": "TAGDL-0264",
        "name": "Well Suited Custom Clothiers 813-545-2700",
        "description": "[\"7.9\", \"4\"]",
        "image": "https://workflow.trinity-apparel.com/images/labels/TAGDL-0264.jpg",
        "options": [
          {
            "id": 1,
            "name": "garment_label",
            "description": "Garment Label",
            "garment_type": 1,
            "garment_types": [
              "csc"
            ]
          }
        ],
        "quantity": 1,
        "dealer_id": 952,
        "size": {
          "width": "7.9",
          "length": "4"
        }
      }
    ]
  },
  "special_instructions": [
    {
        "garment_type": 8,
        "instruction": "The cuff is a non fold french to be used with cufflinks.  3 buttonholes no buttons",
        "translation": null
    }
  ]
}
```

### Description

This call updates or creates a record to match materials to a fabric.

Once the record is created, it will return an updated [garment properties](#garment-properties) JSON that will include these newly matched materials.

### Rules

The ID of at least one material type must be provided (Button, Felt, Thread, Suede). The ID that is passed must also be an active material in our system otherwise an error will be returned.

We will first check for an exsiting fabric match record and update it with the params passed or create a new record if none exists.

To get valid lining IDs, use the [fabric API](#get-all-fabrics) with the following params:

`GET https://api.trinity-apparel.com/v1/fabrics?is_active=1&named_filter=lining&collection_id=1356&pattern_id=1&per_page=32`

For the other materials, use the relevant API call to fetch valid IDs: [Buttons](#get-all-buttons), [Felts](#get-all-felts), [Threads](#get-all-threads), [Suedes](#get-all-suedes).

### HTTP Request

`POST https://api.trinity-apparel.com/v1/garments/:id/fabric_match`

### Query Parameters

| Parameter           | Default | Description                                                                                  |
| ------------------- | ------- | -------------------------------------------------------------------------------------------- |
| id                  | N/A     | The specific garment you want to add a match for the fabric and get an updated properties on |
| lining_fabric_id    | N/A     | The ID of the lining fabric you want to match                                                |
| button_id           | N/A     | The ID of the button you want to match                                                       |
| outerwear_button_id | N/A     | The ID of the outerwear button you want to match                                             |
| felt_id             | N/A     | The ID of the felt you want to match                                                         |
| thread_id           | N/A     | The ID of the thread you want to match                                                       |
| suede_id            | N/A     | The ID of the suede you want to match                                                        |

### Other

- Permissions: Only manufacturers can access this route.
- Pagination: N/A

### Responses

| Response Code | Description                                   |
| ------------- | --------------------------------------------- |
| 200           | Fabric match was successfully updated/created |
| 403           | Not Authorized - You're not a factory         |
| 409           | There was an error. Reason provided in JSON   |
