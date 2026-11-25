---
type: Team
title: Payments
description: Owns charging customers and the ledger.
lead: Maya Chen
channel: '#team-payments'
systems: [/systems/billing-api.md, /systems/ledger.md]
sources:
  - id: systems-billing-api
    resource: /systems/billing-api.md
    title: Billing API
  - id: systems-ledger
    resource: /systems/ledger.md
    title: Ledger
generated:
  by: workflow:update-teams:anthropic/claude-opus-5-5
  at: 2026-11-04T09:30:00Z
stale_after: 2026-12-04T09:30:00Z
verified:
  - by: human:maya@acme.example
    at: 2026-11-05T08:00:00Z
---

Payments owns how Acme charges customers for labels and the ledger behind every balance. Its work this month is making charges safe to retry after the double charges of 2 October.

## Systems

- [Billing API](/systems/billing-api.md): production.
- [Ledger](/systems/ledger.md): production.

## What's changing

- Every [charge carries an idempotency key](../systems/billing-api.md), so a retry can't charge twice.
- The [ledger rejects a second entry](../systems/ledger.md) for the same key.
- [Failed charges are retried 3 times](../systems/billing-api.md), 10 seconds apart.
- Failed charges [keep the processor's response code](../systems/billing-api.md) for support.

## Needs attention

- [Billing API](../systems/billing-api.md) retries drift from Idempotent charges, which requires 5 retries with exponential backoff.
