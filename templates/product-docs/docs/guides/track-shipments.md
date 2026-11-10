---
type: Guide
title: Track a shipment
description: Show customers where their parcel is, from the shipment's status and the carrier's tracking events.
audience: Developers who show delivery status to their customers
endpoints: [/docs/reference/get-shipment.md, /docs/reference/get-tracking.md]
sources:
  - id: reference-get-shipment
    resource: /docs/reference/get-shipment.md
    title: Get a shipment
  - id: reference-get-tracking
    resource: /docs/reference/get-tracking.md
    title: Get tracking
generated:
  by: "workflow:update-guides:anthropic/claude-opus-5-5"
  at: "2026-10-02T09:00:00Z"
stale_after: "2026-11-01T09:00:00Z"
---

Customers want to know where their parcel is. This guide reads a shipment's status and the carrier's tracking events, so you can show both in your app. It's for developers who show delivery status to their customers.

1. **Get the shipment** for its `status`: `created`, `label_purchased`, `in_transit`, `delivered`, `returned` or `cancelled`.[^reference-get-shipment]

   ```bash
   curl https://api.acme.example/v1/shipments/shp_8Kd2 \
     -H "Authorization: Bearer $ACME_API_KEY"
   ```

2. **Get tracking** once the shipment has a label. Events appear after the carrier first scans the parcel, oldest first, each with a time, a status, a description in the carrier's words and, if the carrier says, a location.[^reference-get-tracking]

   ```bash
   curl https://api.acme.example/v1/shipments/shp_8Kd2/tracking \
     -H "Authorization: Bearer $ACME_API_KEY"
   ```

3. **Show the estimate.** `estimated_delivery_date` is the carrier's guess, and is null when the carrier gives none.[^reference-get-tracking]

To avoid asking over and over, register a webhook endpoint for `tracking.updated` and `shipment.delivered` events. See [Receive webhooks](receive-webhooks.md).

## Related

- [Get a shipment](../reference/get-shipment.md)
- [Get tracking](../reference/get-tracking.md)
