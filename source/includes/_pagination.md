# Pagination

<aside class="notice">The Trinity API uses pagination when there are more than 100 entries of a specific resource. Pagination information is provided in the headers rather than the response body, using the [RFC-8288](https://tools.ietf.org/html/rfc8288) standard.</aside>

Users can navigate through pages of results with the following parameters:

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | View a specific page of results; Page starts at 0
per_page | 25 | Specific number of results to return per page

Resources that use pagination:

- Fabrics
- Collections
- Orders
- Garments
