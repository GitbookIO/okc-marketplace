---
type: Support Thread
title: Can a retried webhook arrive after a newer event?
resource: "mock://support/8"
state: closed
opened_at: "2026-10-21T10:05:00Z"
closed_at: "2026-10-21T12:40:00Z"
area: webhooks
channel: chat
---

## Question

If a delivery to our endpoint fails and is retried, can a newer event for the same shipment reach us first?

## Answer

Yes, today it can. Retries go through a separate pool of workers. The team is working on keeping the events for one shipment in order.
