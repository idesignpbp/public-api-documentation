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

## Customer Dashboard

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

## Export Customers

```shell
curl "https://api.trinity-apparel.com/v1/customers/dashboard.csv"
  -H "Authorization Bearer: swaledale"
```

> The above command returns a CSV content-type that is structured like this:

```
id,name,created_at,company,email,street_1,street_2,city,state,zip,country,phone_cell,phone_work,phone_home,fax,first_order_date,last_order_date,total_orders,total_garments

19016,Rapid Replenishment,,,,,,,,,USA,,,,,2013-12-31 17:49:33 UTC,2016-06-30 08:37:18 UTC,2,36

145015,Ben Abernathy,2019-01-05 19:30:25 UTC,,,,,,,,USA,,,,,2019-01-05 13:38:33 UTC,2019-01-05 13:38:33 UTC,1,1

95861,Jeremy Abernathy,2016-10-05 20:38:37 UTC,,,,,,,,USA,,,,,2016-10-05 21:05:33 UTC,2016-10-05 21:05:33 UTC,1,3

2165,Neal Abernathy,,,,,,,AL,,USA,,,,,2006-09-06 09:15:24 UTC,2019-11-15 09:02:38 UTC,26,63

136184,Bill Acton,2018-07-31 16:44:51 UTC,,,,,,,,USA,,,,,2018-08-01 10:57:25 UTC,2019-03-15 15:23:43 UTC,4,8

68625,Jonathon Adams,2015-06-03 15:28:58 UTC,,,,,,,,USA,,,,,2015-06-03 15:50:17 UTC,2018-09-06 15:20:34 UTC,3,5

32446,Tom Addario,,,,,,,,,USA,,,,,2012-04-03 09:25:36 UTC,2013-05-06 10:01:48 UTC,2,3

68169,Ralph Aldridge,2015-05-26 10:28:30 UTC,,,,,,,,USA,,,,,2015-05-29 15:37:13 UTC,2015-05-29 15:37:13 UTC,1,1

105698,Greg Allen,2017-03-25 14:55:44 UTC,,,,,,,,USA,,,,,2017-03-25 15:01:47 UTC,2017-03-28 10:52:51 UTC,2,2

```

Returns a CSV file that lists all of your customers with metrics.  Used on the Trinity clients page.

The first row is a header. Each additional row contains comma delimited data for the following fields:

- id
- name
- created_at
- company
- email
- street_1
- street_2
- city
- state
- zip
- country
- phone_cell
- phone_work
- phone_home
- fax
- first_order_date
- last_order_date
- total_orders
- total_garments

### HTTP Request

`GET https://api.trinity-apparel.com/v1/customers/dashboard.csv`

### Query Parameters

| Parameter  | Default | Description                                                                                                 |
| ---------- | ------- | ----------------------------------------------------------------------------------------------------------- |
| q | N/A     | Fuzzy search. If set, returns only customers with names that contain the search term.       |

### Other

- Permissions: Only includes customers for the dealer who owns the API token
- Pagination: No

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
