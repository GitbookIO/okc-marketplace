---
type: Docs Gap
title: Do webhook events for one shipment arrive in order?
description: The webhook docs don't say whether events for one shipment arrive in order, and the answer changed on 5 November.
state: open
area: webhooks
threads: [/support/mock-3.md, /support/mock-8.md, /support/mock-14.md]
thread_count: 3
sources:
  - id: support-mock-3
    resource: /support/mock-3.md
    title: shipment.delivered arrived before tracking.updated
  - id: support-mock-8
    resource: /support/mock-8.md
    title: Can a retried webhook arrive after a newer event?
  - id: support-mock-14
    resource: /support/mock-14.md
    title: Is the order of webhook events guaranteed now?
  - id: prs-mock-7
    resource: /prs/mock-7.md
    title: Partition the delivery queue by shipment
generated:
  by: "workflow:update-docs-gaps:anthropic/claude-opus-5-5"
  at: "2026-11-06T09:10:00Z"
---

## What customers ask

- [shipment.delivered arrived before tracking.updated](../support/mock-3.md): a team got `shipment.delivered` before the `tracking.updated` event that said the parcel was in transit, and their order status went backwards.
- [Can a retried webhook arrive after a newer event?](../support/mock-8.md): a team asked whether a retried delivery can arrive after a newer event for the same shipment.
- [Is the order of webhook events guaranteed now?](../support/mock-14.md): a team asked for any guarantee about the order of events, since the webhook docs don't say.

## What support answered

Until November, support told [one team](../support/mock-3.md) and [another](../support/mock-8.md) that events can arrive out of order when a delivery is retried, and to compare each event's `created_at` with the last one stored. [The latest answer](../support/mock-14.md) says events for one shipment now arrive in order, but that it isn't documented yet.

## What the docs say

[Create a webhook endpoint](../docs/reference/create-webhook-endpoint.md) and [Receive webhooks](../docs/guides/receive-webhooks.md) explain signatures and retries, and say nothing about order.

## Where the answer is

Since 5 November, [events for one shipment, retries included, arrive in the order they happened](../prs/mock-7.md). Delivery across shipments stays parallel.

```vega-lite
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "description": "Support threads per week asking this question",
  "data": {
    "values": [
      {
        "week": "2026-10-05",
        "threads": 1
      },
      {
        "week": "2026-10-12",
        "threads": 0
      },
      {
        "week": "2026-10-19",
        "threads": 1
      },
      {
        "week": "2026-10-26",
        "threads": 0
      },
      {
        "week": "2026-11-02",
        "threads": 1
      }
    ]
  },
  "mark": "bar",
  "encoding": {
    "x": {
      "field": "week",
      "type": "ordinal",
      "title": "Week starting"
    },
    "y": {
      "field": "threads",
      "type": "quantitative",
      "title": "Threads",
      "axis": {
        "tickMinStep": 1
      }
    }
  }
}
```
