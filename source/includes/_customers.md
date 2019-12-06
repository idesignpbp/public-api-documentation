# Customers API

## Customer Resources

The customers API will return detailed information about customers you have created in Workflow.  Here is a detailed list of attributes in those resources:

### Customer

```json
# Standard Object - Used in a resource collection
{
  "id": 293,
  "name": "Jakob Causey",
  "home_phone": "617-608-2771",
  "cell": "555-555-1234",
  "email": "jakob_upto6@hotmail.com"
}
```

Standard Attributes

| Attribute                           | Description                                 |
| ----------------------------------- | ------------------------------------------- |
| id <br> <span>integer</span>        | Unique identifier for the object.           |
| name <br> <span>string</span>       | The customers first and last name combined. |
| home_phone <br> <span>string</span> | The customer's home phone number.           |
| cell <br> <span>string</span>       | The customer's mobile phone number.         |
| email <br> <span>string</span>      | The customer's email address.               |

```json
# Extended Object
{
    "id": 293,
    "name": "Jakob Causey",
    "first_name": "Jakob",
    "last_name": "Causey",
    "home_phone": "617-608-2771",
    "cell": "555-555-1234",
    "email": "jakob_upto6@hotmail.com",
    "first_name": "Jakob",
    "last_name": "Causey",
    "created_at": "2019-02-13T11:12:56.000Z",
    "address1": "4809 Cedar Lane",
    "address2": null,
    "city": "Boston",
    "state": "MA",
    "zip": "02210",
    "country": "USA",
    "work_phone": null,
    "fax": null,
    "company": "Erlebacher",
    "gender": "male",
    "receive_email_promos": true,
    "receive_mail_promos": true,
    "name_label": "JCausey",
    "laundry_marker": "JCausey",
    "monogram": "JC",
    "notes": "Athletic build",
    "dealer_personal": false
}
```

Extended attributes

| Attribute                                      | Description                                          |
| ---------------------------------------------- | ---------------------------------------------------- |
| first_name <br> <span>string</span>            | The customer's first name.                           |
| last_name <br> <span>string</span>             | The customer's last name.                            |
| created_at <br> <span>datetime</span>          | The date the customer was added to Workflow.         |
| address1 <br> <span>string</span>              | The customer's first address line.                   |
| address2 <br> <span>string</span>              | The customer's second address line.                  |
| city <br> <span>string</span>                  | The city of the customer's address.                  |
| state <br> <span>string</span>                 | The state of the customer's address.                 |
| zip <br> <span>string</span>                   | The zip code of the customer's address.              |
| country <br> <span>string</span>               | The country of the customer's address.               |
| work_phone <br> <span>string</span>            | The customer's work phone number.                    |
| fax <br> <span>string</span>                   | The customer's fax number.                           |
| company <br> <span>string</span>               | The customer's company.                              |
| gender <br> <span>string</span>                | The gender of the customer.                          |
| receive_email_promos <br> <span>boolean</span> | If the customer has opted to receive email promos.   |
| receive_mail_promos <br> <span>boolean</span>  | If the customer has opted to receive mail promos.    |
| name_label <br> <span>string</span>            | The customer's preferred name label.                 |
| laundry_marker <br> <span>string</span>        | The customer's preferred laundry marker.             |
| monogram <br> <span>string</span>              | The customer's preferred monogram.                   |
| notes <br> <span>string</span>                 | Notes about the customer.                            |
| dealer_personal <br> <span>boolean</span>      | If this customer is a personal account of the dealer. |


```json
# Dashboard Object
{
    "id": 121008,
    "first_order": null,
    "last_order": null,
    "name": "Rapid Replenishment",
    "total_orders": 0,
    "total_garments": null
}
```
Dashboard attributes

| Attribute                                      | Description                                          |
| ---------------------------------------------- | ---------------------------------------------------- |
| id <br> <span>integer</span>                   | Unique identifier for the object.                    |
| first_order <br> <span>datetime</span>         | Date of the first order. Null if no orders exist     |
| last_order <br> <span>datetime</span>          | Date of the last order. Null if no orders exist      |
| name <br> <span>string</span>                  | The customers first and last name combined.          |
| total_orders <br> <span>integer</span>         | Lifetime count of dealer orders for this customer    |
| total_garments <br> <span>integer</span>       | Lifetime count of garments ordered by this customer  |


## Get All Customers

```shell
curl "https://api.trinity-apparel.com/v1/customers"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 293,
    "name": "Jakob Causey",
    "first_name": "Jakob",
    "last_name": "Causey",
    "home_phone": "617-608-2771",
    "cell": "555-555-1234",
    "email": "jakob_upto6@hotmail.com"
  },
  {
    "id": 293,
    "name": "Jakob Causey",
    "first_name": "Jakob",
    "last_name": "Causey",
    "home_phone": "617-608-2771",
    "cell": "555-555-1234",
    "email": "jakob_upto6@hotmail.com"
  },
  {
    "id": 293,
    "name": "Jakob Causey",
    "first_name": "Jakob",
    "last_name": "Causey",
    "home_phone": "617-608-2771",
    "cell": "555-555-1234",
    "email": "jakob_upto6@hotmail.com"
  },
  {
    "id": 293,
    "name": "Jakob Causey",
    "first_name": "Jakob",
    "last_name": "Causey",
    "home_phone": "617-608-2771",
    "cell": "555-555-1234",
    "email": "jakob_upto6@hotmail.com"
  },
  {
    "id": 293,
    "name": "Jakob Causey",
    "first_name": "Jakob",
    "last_name": "Causey",
    "home_phone": "617-608-2771",
    "cell": "555-555-1234",
    "email": "jakob_upto6@hotmail.com"
  },
  {
    "id": 293,
    "name": "Jakob Causey",
    "first_name": "Jakob",
    "last_name": "Causey",
    "home_phone": "617-608-2771",
    "cell": "555-555-1234",
    "email": "jakob_upto6@hotmail.com"
  },
  {
    "id": 293,
    "name": "Jakob Causey",
    "first_name": "Jakob",
    "last_name": "Causey",
    "home_phone": "617-608-2771",
    "cell": "555-555-1234",
    "email": "jakob_upto6@hotmail.com"
  },
  {
    "id": 293,
    "name": "Jakob Causey",
    "first_name": "Jakob",
    "last_name": "Causey",
    "home_phone": "617-608-2771",
    "cell": "555-555-1234",
    "email": "jakob_upto6@hotmail.com"
  },
  {
    "id": 293,
    "name": "Jakob Causey",
    "first_name": "Jakob",
    "last_name": "Causey",
    "home_phone": "617-608-2771",
    "cell": "555-555-1234",
    "email": "jakob_upto6@hotmail.com"
  },
  {
    "id": 293,
    "name": "Jakob Causey",
    "first_name": "Jakob",
    "last_name": "Causey",
    "home_phone": "617-608-2771",
    "cell": "555-555-1234",
    "email": "jakob_upto6@hotmail.com"
  },
]
```

Returns an array of your customers.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/customers`

### Query Parameters

| Parameter  | Default | Description                                                                                                 |
| ---------- | ------- | ----------------------------------------------------------------------------------------------------------- |
| q          | N/A     | Fuzzy search. If set, returns only customers with names that contain the search term. |
| first_name | N/A     | If set, will return results with exact matching first_name.                                                 |
| last_name  | N/A     | If set, will return results with exact matching last_name.                                                  |
| email      | N/A     | If set, will return results with exact matching email address.                                              |
| city       | N/A     | If set, will return results with exact matching city.                                                       |
| state      | N/A     | If set, will return results with exact matching state.                                                      |
| zip        | N/A     | If set, will return results with exact matching zip code.                                                   |
| country    | N/A     | If set, will return results with exact matching country.                                                    |
| extended   | false   | If true, the API call returns extended objects which include a complete set of attributes and subresources. |

### Other

- Permissions: Only includes customers for the dealer who owns the API token
- Pagination: Yes

## Get Customers Dashboard

```shell
curl "https://api.trinity-apparel.com/v1/customers/dashboard"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 121008,
        "first_order": null,
        "last_order": null,
        "name": "Rapid Replenishment",
        "total_orders": 0,
        "total_garments": null
    },
    {
        "id": 134420,
        "first_order": "2019-04-21T23:09:04.000Z",
        "last_order": "2019-04-21T23:09:04.000Z",
        "name": "Tony Stark",
        "total_orders": 1,
        "total_garments": 2
    },
    {
        "id": 121009,
        "first_order": "2018-12-09T01:51:41.000Z",
        "last_order": "2019-07-10T03:32:25.000Z",
        "name": "Steve Rogers",
        "total_orders": 3,
        "total_garments": 4
    },
    {
        "id": 156012,
        "first_order": null,
        "last_order": null,
        "name": "Dr. Bruce Banner",
        "total_orders": 0,
        "total_garments": null
    },
    {
        "id": 122123,
        "first_order": null,
        "last_order": null,
        "name": "Peter Parker",
        "total_orders": 0,
        "total_garments": null
    },
    ...
]
```

Returns an array of your customers with metrics.  Used in the Trinity clients page.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/customers/dashboard`

### Query Parameters

| Parameter  | Default | Description                                                                                                 |
| ---------- | ------- | ----------------------------------------------------------------------------------------------------------- |
| q | N/A     | Fuzzy search. If set, returns only customers with names that contain the search term.       |

### Other

- Permissions: Only includes customers for the dealer who owns the API token
- Pagination: Yes

## Get a Specific Customer

```shell
curl "https://api.trinity-apparel.com/v1/customers/293"
  -H "Authorization Bearer: swaledale"
```

> The above command returns JSON structured like this:

```json
{
    "id": 293,
    "name": "Jakob Causey",
    "first_name": "Jakob",
    "last_name": "Causey",
    "home_phone": "617-608-2771",
    "cell": "555-555-1234",
    "email": "jakob_upto6@hotmail.com",
    "created_at": "2019-02-13T11:12:56.000Z",
    "address1": "4809 Cedar Lane",
    "address2": null,
    "city": "Boston",
    "state": "MA",
    "zip": "02210",
    "country": "USA",
    "work_phone": null,
    "fax": null,
    "company": "Erlebacher",
    "gender": "male",
    "receive_email_promos": true,
    "receive_mail_promos": true,
    "name_label": "JCausey",
    "laundry_marker": "JCausey",
    "monogram": "JC",
    "notes": "Athletic build",
    "dealer_personal": false
}
```

Returns details on a specific customer.

### HTTP Request

`GET https://api.trinity-apparel.com/v1/customers/:id`

### Query Parameters

| Parameter | Default | Description                              |
| --------- | ------- | ---------------------------------------- |
| id        | N/A     | The specific customer id you want to see |

### Other

- Permissions: Only includes the customer, if they belong to the dealer who owns the API token
- Pagination: N/A
