---
type: Support Thread
title: Label purchase hangs and returns a 502
resource: "mock://support/7"
state: closed
opened_at: "2026-10-20T13:44:00Z"
closed_at: "2026-10-20T14:30:00Z"
area: labels
channel: chat
---

## Question

Buying a label sometimes hangs for 30 seconds and then returns a 502. If we retry, could we end up buying two labels?

## Answer

Send the retry with the same `Idempotency-Key` header and you'll only be charged once. The team is adding a proper timeout for slow carriers.
