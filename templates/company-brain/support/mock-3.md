---
type: Support Thread
title: Tracking webhooks arrive out of order
resource: "mock://support/3"
account: "/accounts/northline.md"
state: closed
opened_at: "2026-10-09T08:40:00Z"
closed_at: "2026-10-10T10:05:00Z"
area: webhooks
channel: email
---

## Question

We sometimes get `delivered` before `out_for_delivery` for the same shipment, and our system then shows the wrong status.

## Answer

During retries, events for one shipment can arrive out of order. Sort them by `occurred_at` for now. The team is changing delivery so events for one shipment always arrive in order.
