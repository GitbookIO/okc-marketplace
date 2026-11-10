---
type: API Endpoint
title: Create a shipment
description: Create a shipment from an origin, a destination and its parcels.
method: POST
path: /v1/shipments
operation_id: createShipment
sources:
  - id: api-openapi
    resource: /api/openapi.yaml
    title: Acme Shipping API spec
  - id: prs-mock-1
    resource: /prs/mock-1.md
    title: Validate postal codes before creating shipments
  - id: prs-mock-6
    resource: /prs/mock-6.md
    title: Add signature_required to create shipment
generated:
  by: "workflow:sync-reference:anthropic/claude-opus-5-5"
  at: "2026-11-03T15:30:00Z"
stale_after: "2027-02-01T15:30:00Z"
verified:
  - by: "process:contract-tests"
    at: "2026-11-08T02:00:00Z"
---

Creates a shipment from an origin, a destination and one or more parcels. A new shipment has no label yet. Get rates for it, then buy a label with one of them. Destination postal codes are checked against the destination country. A destination postal code that doesn't exist fails here with `invalid_postal_code`, instead of later when the carrier rejects the label.[^prs-mock-1] With `signature_required`, services that charge for signatures quote the higher price in rates.[^prs-mock-6]

## Request

`POST /v1/shipments`

| Parameter | In | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `Idempotency-Key` | header | string | no | A unique value you choose, like a UUID. Sending the same key again within 24 hours returns the first response instead of doing the work twice. |

Body fields:

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `from` | Address | yes | Where the parcel ships from. |
| `to` | Address | yes | Where the parcel is going. |
| `parcels` | array of Parcel | yes | One or more parcels. |
| `signature_required` | boolean, default `false` | no | Ask the carrier to get a signature on delivery. Some services cost more with it. |
| `reference` | string | no | Your own id for the shipment, like an order number. |

### Address

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `name` | string | yes | Person or company name. |
| `street1` | string | yes | Street and number. |
| `street2` | string | no | Apartment, suite or floor. |
| `city` | string | yes | City. |
| `state` | string | no | State or province |
| `postal_code` | string | yes | Postal code. |
| `country` | string | yes | Two-letter ISO 3166-1 country code. |

### Parcel

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `weight_grams` | integer | yes | Weight in grams. |
| `length_cm` | number | no | Length in centimeters. |
| `width_cm` | number | no | Width in centimeters. |
| `height_cm` | number | no | Height in centimeters. |

## Response

`201`: The shipment was created.

| Field | Type | Description |
| --- | --- | --- |
| `id` | string | The shipment id, like shp_8Kd2. |
| `status` | string: `created`, `label_purchased`, `in_transit`, `delivered`, `returned`, `cancelled` | Where the shipment is now. |
| `reference` | string or null | Your own id, if you set one. |
| `signature_required` | boolean | Whether the carrier gets a signature on delivery. |
| `tracking_number` | string or null | Set once a label is bought. |
| `label_id` | string or null | Set once a label is bought. |
| `created_at` | string (date-time) | When the shipment was created. |

## Errors

| Status | Code | When |
| --- | --- | --- |
| 400 | `invalid_request` | The request is missing a field or has one in the wrong format. |
| 409 | `idempotency_conflict` | The Idempotency-Key was already used with a different request body. |
| 422 | `invalid_postal_code` | The destination postal code doesn't exist in the destination country. |

## Example

```bash
curl -X POST https://api.acme.example/v1/shipments \
  -H "Authorization: Bearer $ACME_API_KEY" \
  -H "Idempotency-Key: 8f14e45f-order-4417" \
  -H "Content-Type: application/json" \
  -d '{
    "from": {
      "name": "Acme Warehouse",
      "street1": "1 Dock Road",
      "city": "Rotterdam",
      "postal_code": "3011 AA",
      "country": "NL"
    },
    "to": {
      "name": "Sam Lee",
      "street1": "20 Canal Street",
      "city": "Utrecht",
      "postal_code": "3511 LB",
      "country": "NL"
    },
    "parcels": [
      {
        "weight_grams": 1200,
        "length_cm": 30,
        "width_cm": 20,
        "height_cm": 10
      }
    ],
    "signature_required": true,
    "reference": "order-4417"
  }'
```

```json
{
  "id": "shp_8Kd2",
  "status": "created",
  "reference": "order-4417",
  "signature_required": true,
  "tracking_number": null,
  "label_id": null,
  "created_at": "2026-11-09T09:30:00Z"
}
```

## Changes

- 2026-11-03: [Ask for a signature on delivery](../changelog/2026-11-03-signature-required.md)
- 2026-10-15: [Reject unknown postal codes](../changelog/2026-10-15-invalid-postal-code.md)
