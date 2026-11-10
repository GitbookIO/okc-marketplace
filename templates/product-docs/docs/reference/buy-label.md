---
type: API Endpoint
title: Buy a label
description: Buy a carrier label for one of a shipment's rates.
method: POST
path: /v1/shipments/{id}/label
operation_id: buyLabel
sources:
  - id: api-openapi
    resource: /api/openapi.yaml
    title: Acme Shipping API spec
  - id: prs-mock-3
    resource: /prs/mock-3.md
    title: Time out carrier label calls after 8 seconds
  - id: prs-mock-8
    resource: /prs/mock-8.md
    title: Let callers choose the label format
generated:
  by: "workflow:sync-reference:anthropic/claude-opus-5-5"
  at: "2026-11-06T12:45:00Z"
stale_after: "2027-02-04T12:45:00Z"
verified:
  - by: "process:contract-tests"
    at: "2026-11-08T02:00:00Z"
---

Buys a label from the carrier for one of the shipment's rates, and charges it to your balance. Acme waits up to 8 seconds for the carrier. Retry a request that timed out with the same Idempotency-Key: if the first one went through, you get the same label back and aren't charged twice. Slow carriers used to hold a request for up to 30 seconds and return a 502, which is why it now times out at 8.[^prs-mock-3] `label_format` defaults to `pdf_4x6`, the only format before 1.15.0.[^prs-mock-8]

## Request

`POST /v1/shipments/{id}/label`

| Parameter | In | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | string | yes | The shipment's id, like shp_8Kd2. |
| `Idempotency-Key` | header | string | no | A unique value you choose, like a UUID. Sending the same key again within 24 hours returns the first response instead of doing the work twice. |

Body fields:

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `rate_id` | string | yes | A rate from the shipment's rate quote. |
| `label_format` | string: `pdf_4x6`, `pdf_a4`, `zpl` | no | File format of the label. zpl is for thermal printers. |

## Response

`201`: The label.

| Field | Type | Description |
| --- | --- | --- |
| `id` | string | The label's id. |
| `shipment_id` | string | The shipment it's for. |
| `carrier` | string | Carrier name. |
| `tracking_number` | string | The carrier's tracking number. |
| `label_format` | string: `pdf_4x6`, `pdf_a4`, `zpl` | File format of the label. |
| `label_url` | string (uri) | Where to download the label file. |
| `created_at` | string (date-time) | When the label was bought. |

## Errors

| Status | Code | When |
| --- | --- | --- |
| 404 | `not_found` | Nothing with that id exists in your account. |
| 409 | `label_exists` | The shipment already has a label. |
| 422 | `rate_expired` | The rate is too old to buy. Get rates again and use a new one. |
| 504 | `carrier_timeout` | The carrier didn't answer within 8 seconds. Retry with the same Idempotency-Key. |

## Example

```bash
curl -X POST https://api.acme.example/v1/shipments/shp_8Kd2/label \
  -H "Authorization: Bearer $ACME_API_KEY" \
  -H "Idempotency-Key: 8f14e45f-order-4417" \
  -H "Content-Type: application/json" \
  -d '{
    "rate_id": "rate_71Pq",
    "label_format": "zpl"
  }'
```

```json
{
  "id": "lbl_3Rt9",
  "shipment_id": "shp_8Kd2",
  "carrier": "Parcelline",
  "tracking_number": "PL4829103756",
  "label_format": "zpl",
  "label_url": "https://files.acme.example/labels/lbl_3Rt9.zpl",
  "created_at": "2026-11-09T09:32:00Z"
}
```

## Changes

- 2026-11-06: [Choose the label format](../changelog/2026-11-06-label-format.md)
- 2026-10-26: [Label purchases time out after 8 seconds](../changelog/2026-10-26-label-timeout.md)
