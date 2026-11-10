---
type: Support Thread
title: Is the order of webhook events guaranteed now?
resource: "mock://support/14"
state: closed
opened_at: "2026-11-05T18:05:00Z"
closed_at: "2026-11-06T08:50:00Z"
area: webhooks
channel: email
---

## Question

Is there any guarantee about the order of events for one shipment? We read the webhook docs and they don't say.

## Answer

Engineering just shipped ordering per shipment: events for one shipment now arrive in the order they happened. It isn't in the docs yet, so keep checking `created_at` for now.
