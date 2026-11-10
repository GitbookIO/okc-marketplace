---
type: Docs Gap
title: Do I get the label fee back when I cancel a shipment?
description: The docs say cancelling voids the label, but not whether or when the label fee comes back.
state: open
area: labels
threads: [/support/mock-5.md, /support/mock-12.md, /support/mock-15.md]
thread_count: 3
sources:
  - id: support-mock-5
    resource: /support/mock-5.md
    title: Do we get the label fee back when we cancel?
  - id: support-mock-12
    resource: /support/mock-12.md
    title: Cancelled shipment still shows the label charge
  - id: support-mock-15
    resource: /support/mock-15.md
    title: What happens to the label fee when we cancel?
generated:
  by: "workflow:update-docs-gaps:anthropic/claude-opus-5-5"
  at: "2026-11-06T10:00:00Z"
---

## What customers ask

- A team that cancelled after buying a label asked whether the fee comes back, and when.[^support-mock-5]
- A customer saw the label charge still on their balance a day after cancelling.[^support-mock-12]
- A team building cancellation into their app asked what happens to the fee and whether there's a deadline.[^support-mock-15]

## What support answered

Every answer says the fee goes back to the balance once the carrier confirms the void. They differ on timing: "a few days, and up to 14" in one, "up to 14 days" and "within 14 days" in the others.[^support-mock-5][^support-mock-12][^support-mock-15] Two answers add a rule about scans: labels the carrier already scanned can't be voided, and you can cancel until the carrier scans the parcel.[^support-mock-12][^support-mock-15]

## What the docs say

[Cancel a shipment](../docs/reference/cancel-shipment.md) says Acme asks the carrier to void the label, and nothing about the fee, how long it takes, or labels that were scanned.

```vega-lite
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "description": "Support threads per week asking this question",
  "data": {
    "values": [
      {
        "week": "2026-10-12",
        "threads": 1
      },
      {
        "week": "2026-10-19",
        "threads": 0
      },
      {
        "week": "2026-10-26",
        "threads": 0
      },
      {
        "week": "2026-11-02",
        "threads": 2
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
