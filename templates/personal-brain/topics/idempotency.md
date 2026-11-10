---
type: Topic
title: "Idempotency"
description: "Every charge carries an idempotency key and the Ledger refuses a second entry with the same key, so retries are safe, but how many retries is still in dispute."
aliases: ["Idempotency keys"]
related: ["/topics/zero-downtime-migrations.md"]
sources:
  - id: meetings-mock-3
    resource: "/meetings/mock-3.md"
    title: "Idempotent charges review"
  - id: meetings-mock-6
    resource: "/meetings/mock-6.md"
    title: "Ledger migration sync"
  - id: sources-mock-10
    resource: "/sources/mock-10.md"
    title: "Retries: the RFC and what shipped"
generated:
  by: "workflow:update-topics:anthropic/claude-opus-5-5"
  at: "2026-10-24T12:00:00Z"
stale_after: "2026-11-23T12:00:00Z"
verified:
  - by: "human:maya@acme.example"
    at: "2026-10-26T09:15:00Z"
---

Since the duplicate charges on 2 October, every charge carries an idempotency key, and the Ledger refuses a second entry with the same key and returns the first one instead.[^meetings-mock-3] That makes any retry safe. How many times to retry is in dispute: the RFC and what shipped disagree.[^meetings-mock-6][^sources-mock-10]

## Current understanding

- A retry on 2 October charged some customers twice. The fix is an idempotency key on every charge.[^meetings-mock-3]
- The Ledger refuses a second entry with the same key and returns the first entry instead of an error, so callers can simply retry.[^meetings-mock-3]
- The processor's own deduplication wasn't enough: it lasts 24 hours and doesn't work across its regions. A lock per label purchase wouldn't stop a webhook that arrives twice.[^meetings-mock-3]
- With keys in place, more retries cost only time, and fewer retries leave more failed charges for support to chase.[^sources-mock-10]

## Contradictions

- **How many retries.** The Idempotent charges RFC says a failed charge is retried 5 times, with exponential backoff starting at 2 seconds.[^meetings-mock-6][^sources-mock-10] Billing shipped 3 retries, 10 seconds apart, and the backfill copied that for its ledger writes.[^meetings-mock-6] Neither record says which is meant.

## Open questions

- Which retry policy should the ledger backfill use?[^sources-mock-10]
- Why did billing ship with 3 retries?[^sources-mock-10]

## See also

- [Zero-downtime migrations](zero-downtime-migrations.md)
- [Dev Okafor](../people/dev-okafor.md)
