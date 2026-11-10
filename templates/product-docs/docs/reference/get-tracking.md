---
type: API Endpoint
title: Get tracking
description: Get a shipment's tracking events and estimated delivery date.
method: GET
path: /v1/shipments/{id}/tracking
operation_id: getTracking
sources:
  - id: api-openapi
    resource: /api/openapi.yaml
    title: Acme Shipping API spec
generated:
  by: "workflow:sync-reference:anthropic/claude-opus-5-5"
  at: "2026-10-01T10:00:00Z"
stale_after: "2026-12-30T10:00:00Z"
---

Returns the carrier's tracking events for a shipment, oldest first, and the estimated delivery date. Events appear once the carrier scans the parcel.

## Request

`GET /v1/shipments/{id}/tracking`

| Parameter | In | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | string | yes | The shipment's id, like shp_8Kd2. |

## Response

`200`: Tracking details.

| Field | Type | Description |
| --- | --- | --- |
| `shipment_id` | string | The shipment. |
| `carrier` | string | Carrier name. |
| `tracking_number` | string | The carrier's tracking number. |
| `status` | string: `created`, `label_purchased`, `in_transit`, `delivered`, `returned`, `cancelled` | Latest status. |
| `estimated_delivery_date` | string (date) or null | When the carrier expects to deliver, if it says. |
| `events` | array of objects | Tracking events, oldest first. |

### `events` items

| Field | Type | Description |
| --- | --- | --- |
| `occurred_at` | string (date-time) | When the carrier scanned the parcel. |
| `status` | string: `created`, `label_purchased`, `in_transit`, `delivered`, `returned`, `cancelled` | Status after this event. |
| `description` | string | What happened, in the carrier's words. |
| `location` | string or null | Where, if the carrier says. |

## Errors

| Status | Code | When |
| --- | --- | --- |
| 404 | `not_found` | Nothing with that id exists in your account. |

## Example

```bash
curl https://api.acme.example/v1/shipments/shp_8Kd2/tracking \
  -H "Authorization: Bearer $ACME_API_KEY"
```

```json
{
  "shipment_id": "shp_8Kd2",
  "carrier": "Parcelline",
  "tracking_number": "PL4829103756",
  "status": "in_transit",
  "estimated_delivery_date": "2026-11-11",
  "events": [
    {
      "occurred_at": "2026-11-09T16:05:00Z",
      "status": "in_transit",
      "description": "Picked up by the carrier",
      "location": "Rotterdam"
    }
  ]
}
```

## Changes

None since this page was first written.
