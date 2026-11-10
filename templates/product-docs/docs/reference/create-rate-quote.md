---
type: API Endpoint
title: Get rates
description: Get every carrier rate for a shipment, cheapest first.
method: POST
path: /v1/rates
operation_id: createRateQuote
sources:
  - id: api-openapi
    resource: /api/openapi.yaml
    title: Acme Shipping API spec
generated:
  by: "workflow:sync-reference:anthropic/claude-opus-5-5"
  at: "2026-10-01T10:00:00Z"
stale_after: "2026-12-30T10:00:00Z"
verified:
  - by: "process:contract-tests"
    at: "2026-11-08T02:00:00Z"
---

Quotes every carrier service that can take the shipment, cheapest first. Buy a label with the id of one of the rates.

## Request

`POST /v1/rates`

Body fields:

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `shipment_id` | string | yes | The shipment to quote. |

## Response

`200`: The rate quote.

| Field | Type | Description |
| --- | --- | --- |
| `id` | string | The quote's id. |
| `shipment_id` | string | The shipment it quotes. |
| `rates` | array of Rate | Every service that can take the shipment, cheapest first. |
| `created_at` | string (date-time) | When the rates were quoted. |

### Rate

| Field | Type | Description |
| --- | --- | --- |
| `id` | string | Pass it to Buy a label as rate_id. |
| `carrier` | string | Carrier name. |
| `service` | string | The carrier's service level. |
| `amount` | string | Price as a decimal string |
| `currency` | string | Three-letter ISO 4217 code. |
| `estimated_days` | integer | Business days the carrier expects delivery to take. |

## Errors

| Status | Code | When |
| --- | --- | --- |
| 404 | `not_found` | Nothing with that id exists in your account. |

## Example

```bash
curl -X POST https://api.acme.example/v1/rates \
  -H "Authorization: Bearer $ACME_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "shipment_id": "shp_8Kd2"
  }'
```

```json
{
  "id": "rq_5Gh1",
  "shipment_id": "shp_8Kd2",
  "rates": [
    {
      "id": "rate_71Pq",
      "carrier": "Parcelline",
      "service": "Standard",
      "amount": "6.95",
      "currency": "EUR",
      "estimated_days": 2
    },
    {
      "id": "rate_71Pr",
      "carrier": "Swiftway",
      "service": "Express",
      "amount": "12.40",
      "currency": "EUR",
      "estimated_days": 1
    }
  ],
  "created_at": "2026-11-09T09:31:00Z"
}
```

## Changes

None since this page was first written.
