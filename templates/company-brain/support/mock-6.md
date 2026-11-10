---
type: Support Thread
title: Getting timeout errors on every label
resource: "mock://support/6"
account: "/accounts/kestrel.md"
state: closed
opened_at: "2026-10-24T14:05:00Z"
closed_at: "2026-10-25T08:30:00Z"
area: labels
channel: email
---

## Question

Our warehouse can't print a single label. We're getting `carrier_timeout` on every request.

## Answer

Labels have gone through since 14:10. Calls to Parcelline now time out after 8 seconds and return a retryable error, so your retries work. Your account manager will be in touch about the sale.
