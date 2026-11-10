---
type: Meeting
title: "Idempotent charges review"
resource: "mock://meetings/3"
date: 2026-10-12
attendees: [Maya Chen, Dev Okafor, Ana Kovac]
duration_minutes: 45
---

## Summary

- After the duplicate charges on 2 October, every charge will carry an idempotency key, and the Ledger refuses a second entry with the same key.
- The other options were asking the payment processor to dedupe and a lock per label purchase.
- Action: Maya writes the RFC.

## Transcript

**Maya Chen:** On 2 October a retry charged some customers twice. I see three ways out: idempotency keys on every charge, the processor deduping for us, or a lock per label purchase.

**Ana Kovac:** The processor only dedupes for 24 hours, and not across its regions.

**Dev Okafor:** A lock fixes our own retries, but not a webhook that arrives twice.

**Maya Chen:** Keys, then. And the Ledger refuses a second entry with the same key, so it holds even if billing slips.

**Dev Okafor:** If the Ledger returns the first entry instead of an error, callers can just retry.

**Maya Chen:** Agreed. I'll write the RFC.
