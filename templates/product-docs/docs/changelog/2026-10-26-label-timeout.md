---
type: Changelog Entry
title: Label purchases time out after 8 seconds
description: Buy a label returns carrier_timeout after 8 seconds, and accepts an Idempotency-Key.
date: "2026-10-26"
api_version: "1.12.0"
change: added
breaking: false
endpoints: [/docs/reference/buy-label.md]
sources:
  - id: api-openapi
    resource: /api/openapi.yaml
    title: Acme Shipping API spec
  - id: prs-mock-3
    resource: /prs/mock-3.md
    title: Time out carrier label calls after 8 seconds
generated:
  by: "workflow:sync-reference:anthropic/claude-opus-5-5"
  at: "2026-10-26T11:45:00Z"
---

Buy a label waits up to 8 seconds for the carrier, then returns a 504 with `carrier_timeout`. Slow carriers used to hold the request for up to 30 seconds and return a 502. Buy a label also accepts the `Idempotency-Key` header now.[^prs-mock-3]

## What to do

Retry a `carrier_timeout` with the same `Idempotency-Key`. If the first request went through, you get the same label back and aren't charged twice. See [Buy a label](../reference/buy-label.md).
