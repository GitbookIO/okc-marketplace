---
type: Support Thread
title: We keep getting rate_expired on batch label runs
resource: "mock://support/4"
state: closed
opened_at: "2026-10-13T16:20:00Z"
closed_at: "2026-10-14T09:05:00Z"
area: rates
channel: email
---

## Question

Our warehouse buys labels in two batches a day, using the rates we got when each order came in. A lot of them fail with `rate_expired`. Is there a documented validity period for a rate?

## Answer

It isn't documented yet. From what engineering told me, a rate lasts about an hour. Get rates within the hour before each batch and you won't see the error.
