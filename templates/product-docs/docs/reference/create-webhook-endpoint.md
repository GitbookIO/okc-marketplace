---
type: API Endpoint
title: Create a webhook endpoint
description: Register a URL to receive events, and learn how deliveries are signed and retried.
method: POST
path: /v1/webhook_endpoints
operation_id: createWebhookEndpoint
sources:
  - id: api-openapi
    resource: /api/openapi.yaml
    title: Acme Shipping API spec
  - id: prs-mock-5
    resource: /prs/mock-5.md
    title: Cap delivery retries at 5 attempts
generated:
  by: "workflow:sync-reference:anthropic/claude-opus-5-5"
  at: "2026-10-30T12:30:00Z"
stale_after: "2027-01-28T12:30:00Z"
---

Registers a URL that Acme sends events to. The response has the endpoint's signing secret, which is shown only once. Every delivery has an Acme-Signature header: the hex HMAC SHA-256 of the raw request body, keyed with that secret. Check it before you trust the body. A delivery fails when your server doesn't answer with a 2xx status within 10 seconds. Failed deliveries are retried 5 times over about 2 hours, with growing gaps, and then marked as failed. Retries stop after about 2 hours so that endpoints that are down for a day no longer fill the delivery queue.[^prs-mock-5]

## Request

`POST /v1/webhook_endpoints`

Body fields:

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `url` | string (uri) | yes | HTTPS URL to send events to. |
| `events` | array of strings | yes | Event types to send. |

## Response

`201`: The endpoint, with its secret.

| Field | Type | Description |
| --- | --- | --- |
| `id` | string | The endpoint's id. |
| `url` | string (uri) | Where events are sent. |
| `events` | array of strings | Event types it receives. |
| `secret` | string | Signing secret. Only returned when the endpoint is created. |
| `created_at` | string (date-time) | When it was created. |

## Errors

| Status | Code | When |
| --- | --- | --- |
| 400 | `invalid_request` | The URL isn't HTTPS, or an event type doesn't exist. |

## Events

| Event | When |
| --- | --- |
| `shipment.created` | A shipment was created. |
| `label.purchased` | A label was bought for a shipment. |
| `tracking.updated` | The carrier scanned the parcel and tracking has a new event. |
| `shipment.delivered` | The carrier delivered the parcel. |
| `shipment.returned` | The parcel is on its way back to the sender. |

Every event has these fields:

| Field | Type | Description |
| --- | --- | --- |
| `id` | string | Unique per event. Use it to ignore a delivery you already handled. |
| `type` | string: `shipment.created`, `label.purchased`, `tracking.updated`, `shipment.delivered`, `shipment.returned` | The event type. |
| `created_at` | string (date-time) | When it happened. |
| `data` | object | The shipment, label or tracking details the event is about. |

## Example

```bash
curl -X POST https://api.acme.example/v1/webhook_endpoints \
  -H "Authorization: Bearer $ACME_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "url": "https://example.com/acme/webhooks",
    "events": [
      "tracking.updated",
      "shipment.delivered"
    ]
  }'
```

```json
{
  "id": "we_2Lm8",
  "url": "https://example.com/acme/webhooks",
  "events": [
    "tracking.updated",
    "shipment.delivered"
  ],
  "secret": "whsec_9f3kQ",
  "created_at": "2026-11-09T09:40:00Z"
}
```

## Changes

- 2026-10-30: [Webhook retries stop after 5 attempts](../changelog/2026-10-30-webhook-retries.md)
