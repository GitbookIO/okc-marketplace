---
type: Support Thread
title: shipment.delivered arrived before tracking.updated
resource: "mock://support/3"
state: closed
opened_at: "2026-10-09T08:47:00Z"
closed_at: "2026-10-09T11:02:00Z"
area: webhooks
channel: email
---

## Question

For one shipment we got `shipment.delivered` before the `tracking.updated` event that said it was in transit, so our order status went backwards. Are webhook events sent in order?

## Answer

Events can arrive out of order when a delivery is retried. For now, compare each event's `created_at` with the last one you stored for that shipment, and ignore older ones.
