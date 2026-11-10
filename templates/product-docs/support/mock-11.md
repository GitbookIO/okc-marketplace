---
type: Support Thread
title: How do I check the Acme-Signature header?
resource: "mock://support/11"
state: closed
opened_at: "2026-10-30T09:10:00Z"
closed_at: "2026-10-30T09:20:00Z"
area: webhooks
channel: chat
---

## Question

Where do I find how to verify the `Acme-Signature` header on webhook deliveries?

## Answer

It's step 3 of the Receive webhooks guide: compute an HMAC SHA-256 of the raw request body with your endpoint's secret and compare it with the header.
