---
type: Docs Gap
title: Is it safe to retry a label purchase that timed out?
description: Customers didn't know whether retrying a slow label purchase could buy a second label.
state: resolved
area: labels
threads: [/support/mock-7.md, /support/mock-9.md]
thread_count: 2
resolved_by: /docs/reference/buy-label.md
sources:
  - id: reference-buy-label
    resource: /docs/reference/buy-label.md
    title: Buy a label
  - id: support-mock-7
    resource: /support/mock-7.md
    title: Label purchase hangs and returns a 502
  - id: support-mock-9
    resource: /support/mock-9.md
    title: Is it safe to retry a label purchase after a timeout?
generated:
  by: "workflow:resolve-gaps:anthropic/claude-opus-5-5"
  at: "2026-10-26T13:00:00Z"
---

## Resolved

[Buy a label](../docs/reference/buy-label.md) answers it since 26 October 2026: "Retry a request that timed out with the same Idempotency-Key: if the first one went through, you get the same label back and aren't charged twice."[^reference-buy-label]

## What customers ask

- A label purchase hung for 30 seconds and returned a 502, and the team asked whether a retry could buy two labels.[^support-mock-7]
- A team that couldn't tell whether a timed-out request bought a label asked how to retry safely, since the docs only showed `Idempotency-Key` on create shipment.[^support-mock-9]

## What support answered

Both answers said to retry with the same `Idempotency-Key`, and that label purchases accept it even though the reference didn't show it.[^support-mock-7][^support-mock-9]

## What the docs say

Buy a label didn't list `Idempotency-Key`, and didn't say what happens when the carrier is slow.
