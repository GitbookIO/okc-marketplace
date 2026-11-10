---
type: Docs Gap
title: How long is a rate quote valid?
description: The docs never say how long a quote's rates can be bought, only that old ones fail with rate_expired.
state: open
area: rates
threads: [/support/mock-1.md, /support/mock-4.md, /support/mock-10.md, /support/mock-13.md]
thread_count: 4
sources:
  - id: support-mock-1
    resource: /support/mock-1.md
    title: How long can we hold a rate before buying the label?
  - id: support-mock-4
    resource: /support/mock-4.md
    title: We keep getting rate_expired on batch label runs
  - id: support-mock-10
    resource: /support/mock-10.md
    title: How long can we cache a rate quote?
  - id: support-mock-13
    resource: /support/mock-13.md
    title: Could the rate quote say when it expires?
  - id: prs-mock-4
    resource: /prs/mock-4.md
    title: Cache carrier rates for an hour
generated:
  by: "workflow:update-docs-gaps:anthropic/claude-opus-5-5"
  at: "2026-11-05T10:15:00Z"
---

## What customers ask

- A checkout that buys labels up to a day after showing rates got `rate_expired` and asked how long a rate is good for.[^support-mock-1]
- A warehouse that buys labels in two batches a day asked for a documented validity period.[^support-mock-4]
- A team asked how long they can keep a quote for a checkout session.[^support-mock-10]
- A team asked whether the rates response could say when a quote expires, since their checkout shows prices it can't buy.[^support-mock-13]

## What support answered

The first answer said rates change and to get new ones right before buying, without a number.[^support-mock-1] Later answers gave one: about an hour, then exactly one hour from the quote's `created_at`.[^support-mock-4][^support-mock-10][^support-mock-13]

## What the docs say

[Get rates](../docs/reference/create-rate-quote.md) says nothing about how long a quote lasts, and the quote has no expiry field. [Buy a label](../docs/reference/buy-label.md) lists `rate_expired` as "The rate is too old to buy" without saying how old is too old. [Get rates and buy a label](../docs/guides/rates-and-labels.md) says what to do after `rate_expired`, not how to avoid it.

## Where the answer is

Since 29 October, a quote's rates can be bought for one hour after its `created_at`. The pull request also suggests adding an expiry time to the quote.[^prs-mock-4]

```vega-lite
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "description": "Support threads per week asking this question",
  "data": {
    "values": [
      {
        "week": "2026-09-28",
        "threads": 1
      },
      {
        "week": "2026-10-05",
        "threads": 0
      },
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
        "threads": 1
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
