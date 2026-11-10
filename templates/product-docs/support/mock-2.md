---
type: Support Thread
title: What's the largest page size for list shipments?
resource: "mock://support/2"
state: closed
opened_at: "2026-10-06T14:03:00Z"
closed_at: "2026-10-06T15:20:00Z"
area: shipments
channel: email
---

## Question

We export every shipment to our warehouse system each night. `GET /v1/shipments?limit=500` returns a 400. What's the largest page size we can ask for?

## Answer

The limit is 100 per page today, with `offset` to move through pages. The team is working on cursor pagination with larger pages.
