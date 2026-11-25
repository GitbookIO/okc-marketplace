---
type: Topic
title: "Idempotency"
description: "Every charge carries an idempotency key and the Ledger refuses a repeat, so retries are safe. How many retries is still open."
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

Since the duplicate charges on 2 October, every charge carries an idempotency key, and the Ledger refuses a second entry with the same key and hands back the first one. ([Idempotent charges review](../meetings/mock-3.md)) So a retry is always safe. What you don't know yet is how many times to retry, because the RFC and what shipped disagree. ([Ledger migration sync](../meetings/mock-6.md), [Retries: the RFC and what shipped](../sources/mock-10.md))

## Current understanding

- A retry on 2 October charged some customers twice. The fix: an idempotency key on every charge. ([Idempotent charges review](../meetings/mock-3.md))
- The Ledger returns the first entry instead of an error, so callers can just retry. ([Idempotent charges review](../meetings/mock-3.md))
- Why not the alternatives: the processor only dedupes for 24 hours and not across its regions, and a lock per label purchase doesn't stop a webhook arriving twice. ([Idempotent charges review](../meetings/mock-3.md))
- With keys, more retries only cost time. Fewer retries means more failed charges for support to chase. ([Retries: the RFC and what shipped](../sources/mock-10.md))

## Contradictions

- **How many retries.** The Idempotent charges RFC says a failed charge is retried 5 times, with exponential backoff from 2 seconds. ([Ledger migration sync](../meetings/mock-6.md), [Retries: the RFC and what shipped](../sources/mock-10.md)) Billing shipped 3 retries 10 seconds apart, and the backfill copied that. ([Ledger migration sync](../meetings/mock-6.md)) Neither says which one was meant.

## Open questions

- What should the backfill use? You lean toward the RFC. ([Retries: the RFC and what shipped](../sources/mock-10.md))
- Why did billing ship with 3? ([Retries: the RFC and what shipped](../sources/mock-10.md))

## See also

- [Zero-downtime migrations](zero-downtime-migrations.md)
- [Dev Okafor](../people/dev-okafor.md)
