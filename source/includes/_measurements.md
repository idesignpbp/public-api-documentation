# Measurements API

## Measurement Resources

### Measurement Group

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
| garment_type <br> <span>string</span>   | Type of garment. [Click here](#garment-types) for more info |
| display_order <br> <span>integer</span> | The order in which the option is displayed in Workflow. |

### Option

```json
# Standard Object - Used in a resource collection
{
    "id": 1,
    "name": "garment_label",
    "description": "Garment Label",
    "display_order": 5,
    "garment_type": 545,
    "tailoring_grade": 895,
    "order_type": 1,
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
