---
type: API Endpoint
title: List shipments
description: List your shipments, newest first, one page at a time.
method: GET
path: /v1/shipments
operation_id: listShipments
sources:
  - id: api-openapi
    resource: /api/openapi.yaml
    title: Acme Shipping API spec
  - id: prs-mock-2
    resource: /prs/mock-2.md
    title: Add cursor pagination to list shipments
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

Lists your shipments, newest first, one page at a time. Pass the `next_cursor` from a page as `cursor` to get the next one. Filters from the first request apply to every page. `next_cursor` is null on the last page. Cursors don't skip shipments created while you page, which offset pages did.[^prs-mock-2] Every shipment says in `signature_required` whether the carrier gets a signature on delivery.[^prs-mock-6]

## Request

`GET /v1/shipments`

| Parameter | In | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `limit` | query | integer, 1 to 200, default `50` | no | Shipments per page. |
| `cursor` | query | string | no | The next_cursor from the previous page. |
| `status` | query | string: `created`, `label_purchased`, `in_transit`, `delivered`, `returned`, `cancelled` | no | Only shipments with this status. |
| `created_after` | query | string (date-time) | no | Only shipments created after this time. |
| `offset` | query | integer | no | Deprecated. Use cursor. Skips this many shipments, and only works with limit up to 100. |

## Response

`200`: One page of shipments.

| Field | Type | Description |
| --- | --- | --- |
| `data` | array of Shipment | The items on this page. |
| `next_cursor` | string or null | Cursor for the next page, or null on the last page. |

### Shipment

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
| 400 | `invalid_cursor` | The cursor is malformed or came from a request with other filters. |

## Example

```bash
curl https://api.acme.example/v1/shipments?limit=200&status=in_transit \
  -H "Authorization: Bearer $ACME_API_KEY"
```

```json
{
  "data": [
    {
      "id": "shp_8Kd2",
      "status": "in_transit",
      "reference": "order-4417",
      "signature_required": true,
      "tracking_number": "PL4829103756",
      "label_id": "lbl_3Rt9",
      "created_at": "2026-11-09T09:30:00Z"
    }
  ],
  "next_cursor": "c2hwXzhLZDI"
}
```

## Changes

- 2026-11-03: [Ask for a signature on delivery](../changelog/2026-11-03-signature-required.md)
- 2026-10-22: [Page through shipments with a cursor](../changelog/2026-10-22-cursor-pagination.md)
