---
type: API Endpoint
title: Get a shipment
description: Get one shipment and its current status.
method: GET
path: /v1/shipments/{id}
operation_id: getShipment
sources:
  - id: api-openapi
    resource: /api/openapi.yaml
    title: Acme Shipping API spec
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

Returns one shipment with its current status. Every shipment says in `signature_required` whether the carrier gets a signature on delivery.[^prs-mock-6]

## Request

`GET /v1/shipments/{id}`

| Parameter | In | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | string | yes | The shipment's id, like shp_8Kd2. |

## Response

`200`: The shipment.

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
| 404 | `not_found` | Nothing with that id exists in your account. |

## Example

```bash
curl https://api.acme.example/v1/shipments/shp_8Kd2 \
  -H "Authorization: Bearer $ACME_API_KEY"
```

```json
{
  "id": "shp_8Kd2",
  "status": "label_purchased",
  "reference": "order-4417",
  "signature_required": true,
  "tracking_number": "PL4829103756",
  "label_id": "lbl_3Rt9",
  "created_at": "2026-11-09T09:30:00Z"
}
```

## Changes

- 2026-11-03: [Ask for a signature on delivery](../changelog/2026-11-03-signature-required.md)
