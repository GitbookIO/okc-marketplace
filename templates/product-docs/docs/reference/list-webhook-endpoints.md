---
type: API Endpoint
title: List webhook endpoints
description: List your webhook endpoints.
method: GET
path: /v1/webhook_endpoints
operation_id: listWebhookEndpoints
sources:
  - id: api-openapi
    resource: /api/openapi.yaml
    title: Acme Shipping API spec
generated:
  by: "workflow:sync-reference:anthropic/claude-opus-5-5"
  at: "2026-10-01T10:00:00Z"
stale_after: "2026-12-30T10:00:00Z"
---

Lists your webhook endpoints. Secrets aren't included.

## Request

`GET /v1/webhook_endpoints`

## Response

`200`: Every endpoint.

| Field | Type | Description |
| --- | --- | --- |
| `data` | array of WebhookEndpoint | The items on this page. |

### WebhookEndpoint

| Field | Type | Description |
| --- | --- | --- |
| `id` | string | The endpoint's id. |
| `url` | string (uri) | Where events are sent. |
| `events` | array of strings | Event types it receives. |
| `secret` | string | Signing secret. Only returned when the endpoint is created. |
| `created_at` | string (date-time) | When it was created. |

## Example

```bash
curl https://api.acme.example/v1/webhook_endpoints \
  -H "Authorization: Bearer $ACME_API_KEY"
```

```json
{
  "data": [
    {
      "id": "we_2Lm8",
      "url": "https://example.com/acme/webhooks",
      "events": [
        "tracking.updated",
        "shipment.delivered"
      ],
      "created_at": "2026-11-09T09:40:00Z"
    }
  ]
}
```

## Changes

None since this page was first written.
