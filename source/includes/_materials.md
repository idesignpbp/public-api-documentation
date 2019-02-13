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