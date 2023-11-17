# Changelog

A history of changes to the Trinity Apparel API.

## 2023-11-16
- Updated [get shipment detail](#get-shipment-detail) to include the shipment type (bulk or direct).
- Added API to [get garment ship destination](#get-garment-ship-destination) which includes the shipping class and rack code.
- Added API to [complete shipment](#complete-shipment) that completes a created shipment and adjusts the shipment and garment statuses accordingly.

## 2022-12-05

- Updated [set delay status](#set-delay-status) API to allow for optional notes param.
- Updated [buttons](#garment-properties-materials) garment properties API to also provide an array of options that use the buttons. This is a breaking change as the shape of the `quantity` field for buttons has changed (please see example linked).

## 2022-10-27

Several updates to Materials API:

- Updated [resources](#material-resources).
- Added APIs to [get all pipings](#get-all-pipings) and [get a specific piping](#get-a-specific-piping).
- Added APIs to [get all trouser trims](#get-all-trouser-trims) and [get a specific trouser trim](#get-a-specific-trouser-trim).
- Added APIs to [get all zippers](#get-all-zippers) and [get a specific zipper](#get-a-specific-zipper).

## 2022-06-01

New API to create/update [fabric matches](#update-fabric-match) for a fabric.

## 2021-04-22

New API created to change the [delay status](#set-delay-status) on a garment.

## 2021-04-02

A lot of changes to [fabrics](#fabric-resources) API. Read through the resources and related calls carefully as the data structure has changed for fabrics. The most notable change is that in_stock, restock_date, last_stock_edit_date, and readiness have been combined under a new attribute called factories as these statuses can be different depending on the factory being ordered from.

Also, a new ability to see a collection of your favorite fabrics has been added to the [collection](#get-a-specific-collection) API. Simply pass `favorites` in place of `:id`.

## 2021-02-25

Added new API for manufacturers to [update fabric inventory](#update-inventory).

## 2020-11-11

Added the ability to [Accept](#accept-cmt-fabric) and [Reject](#reject-cmt-fabric) CMT fabrics. This process is almost identical to accepting and rejecting single-length fabrics, but does have a few minor differences that require a different API call.

## 2020-11-06

[Fabric Cut API](#create-fabric-cut) will no longer move a garment to cutting automatically. Garment will now require being moved to cutting manually.

## 2020-10-15

Added `material_type` to [fabric order](#get-fabric-order) API.

## 2020-10-12

Added `material_type` to [fabric](#fabric) API.

## 2020-09-28

Added `special_instructions` array to [garment properties](#garment-properties) API.

## 2020-09-09

Added additional filtering on [customer dashboard](#customer-dashboard). Can now filter on if customers have or have not ordered certain garment types within a date range.

## 2020-09-01

On download_garments API call, the outgoing address now also provides the contact name.

## 2020-08-06

- Manufacturers can now view all fabric shipments (shipments containing fabric orders) and filter by status (pending, transit, received)
  - Route is `GET /fabric_shipments`

## 2020-07-23

Added missing params for accepting a fabric order and added explantion on when they need to be included.

## 2020-07-22

Added Fabric Composition to `GET /fabric_orders/:id`

## 2020-06-17

Manufacturers can now manage fabric orders and fabric shipments from suppliers using the new Shipments API:

- Fabric Shipments
  - `GET /shipments/:id` now also returns fabric orders related to a shipment.
  - `POST /shipments/:id/receive` - receive fabric shipments
- Fabric Orders
  - `GET /fabric_orders/:id` - view details on a fabric order
  - `POST /fabric_orders/:id/receive` - receive a fabric order
  - `POST /fabric_orders/:id/accept` - accept a fabric order
  - `POST /fabric_orders/:id/reject` - reject a fabric order
  - `POST /fabric_orders/:id/errors` - identify small errors (spots, tears) on a received fabric order

## 2020-06-02

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
  - Fabric search has been updated to only return fabrics that are connected to a manufacturer that you are set up with. E.g., if you are not set up for MTO, you cannot see MTO fabrics.

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
  - _Seen in [Garment Properties](#garment-properties) route_

## 2020-01-14

- Factory shipping address
  - Show outgoing address that the factory should ship to
  - stored under `outgoing_address` in the JSON response
  - no more guessing based on garment prefix
  - _Seen in [Download Garments](#download-garments) route_

## 2020-01-08

- UPDATE - Fabric pattern measurements
  - Data model changed to use pattern_type, pattern_length, length_offset, pattern_width, and width_offset fields
  - Business rules on when pattern_length and pattern_width are required were modified
  - _Seen in [Update Fabric](#update-fabric) route_

## 2020-01-03

- Order filtering
  - Can now filter order metrics by customer_id
  - _Seen in [Order Metrics](#order-metrics) route_

## Older Changes

Unfortunately, there is no more changelog history at this time.
