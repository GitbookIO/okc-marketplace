---
type: Support Thread
title: Is it safe to retry a label purchase after a timeout?
resource: "mock://support/9"
state: closed
opened_at: "2026-10-24T15:50:00Z"
closed_at: "2026-10-25T08:30:00Z"
area: labels
channel: email
---

## Question

When a label request times out on our side, we don't know whether the label was bought. What's the safe way to retry? The docs only list the Idempotency-Key header on create shipment.

## Answer

Use the same `Idempotency-Key` as the first request. If that one went through, you get the same label back and no second charge. Label purchases accept the header even though the reference doesn't show it yet.
