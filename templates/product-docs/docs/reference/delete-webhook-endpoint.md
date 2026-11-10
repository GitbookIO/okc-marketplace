---
type: API Endpoint
title: Delete a webhook endpoint
description: Delete a webhook endpoint and stop its deliveries.
method: DELETE
path: /v1/webhook_endpoints/{id}
operation_id: deleteWebhookEndpoint
sources:
  - id: api-openapi
    resource: /api/openapi.yaml
    title: Acme Shipping API spec
generated:
  by: "workflow:sync-reference:anthropic/claude-opus-5-5"
  at: "2026-10-01T10:00:00Z"
stale_after: "2026-12-30T10:00:00Z"
---

Stops sending events to an endpoint and deletes it. Deliveries already queued are dropped.

## Request

`DELETE /v1/webhook_endpoints/{id}`

| Parameter | In | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | string | yes | The endpoint's id. |

## Response

`204`: The endpoint was deleted.

## Errors

| Status | Code | When |
| --- | --- | --- |
| 404 | `not_found` | Nothing with that id exists in your account. |

## Example

```bash
curl -X DELETE https://api.acme.example/v1/webhook_endpoints/we_2Lm8 \
  -H "Authorization: Bearer $ACME_API_KEY"
```

The response has no body.

## Changes

None since this page was first written.
