# Changelog

A history of changes to the Trinity Apparel API.

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