# Changelog

A history of changes to the Trinity Apparel API.

## Coming Soon :: Expected 2020-06-02

- Garment Properties - Buttons
  - Buttons sizes use the Ligne scale instead of small/large
  - Suspender buttons now appear in the same array as normal buttons. They are no longer a separate key under materials.
  - Suspender buttons have a `type` field that indicates the color and function of the button (eg: Black Suspender Button). Suspender button quantities also use the Ligne scale.
  - The button calculator has been extended to provide button quantities for MTM Jackets, Trousers, Vests, and Shirts

## 2020-05-28

- Garment Properties
  - Dealer labels are now included in the materials hash

## 2020-04-16

- User Permissions
  - The /login route has been extended to provide dealer permissions
  - This allows us to draw the navigation bar in React

## 2020-04-10

- Create Customers
  - Added the POST `/v1/customers` route
  - Dealers can create customers using a name and email address

## 2020-02-27

- Fabric Search
  - Fabric search has been updated to only return fabrics that are connected to a manufacturer that you are set up with.  E.g., if you are not set up for MTO, you cannot see MTO fabrics.

## 2020-01-20

```
# Documentation

- Added Changelog
- Added docs on [Order Metrics](#order-metrics) route
- Added docs on fabric usage in garment properties and factory shipping address
```

- Fabric usage
  - Categorize fabrics within a garment by usage (shell, lining, trim, etc)
  - its now easier to filter fabric results
  - *Seen in [Garment Properties](#garment-properties) route*

## 2020-01-14

- Factory shipping address
  - Show outgoing address that the factory should ship to
  - stored under `outgoing_address` in the JSON response
  - no more guessing based on garment prefix
  - *Seen in [Download Garments](#download-garments) route*

## 2020-01-08

- UPDATE - Fabric pattern measurements
  - Data model changed to use pattern_type, pattern_length, length_offset, pattern_width, and width_offset fields
  - Business rules on when pattern_length and pattern_width are required were modified
  - *Seen in [Update Fabric](#update-fabric) route*

## 2020-01-03

- Order filtering
  - Can now filter order metrics by customer_id
  - *Seen in [Order Metrics](#order-metrics) route*

## Older Changes

Unfortunately, there is no more changelog history at this time.