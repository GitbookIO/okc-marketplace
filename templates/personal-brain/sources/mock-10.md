---
type: Source
title: "Retries: the RFC and what shipped"
resource: "mock://sources/10"
kind: note
captured_at: "2026-10-24T11:20:00Z"
author: Maya Chen
---

## Summary

The Idempotent charges RFC says a failed charge is retried 5 times with exponential backoff, and billing shipped 3 retries 10 seconds apart. With idempotency keys a retry is always safe. Open: which the backfill should use, and why billing shipped with 3.

## Note

Thinking about retries after Tuesday's sync.

- The Idempotent charges RFC says a failed charge is retried 5 times, with exponential backoff starting at 2 seconds.
- What shipped in billing, per Dev: 3 retries, 10 seconds apart.
- With idempotency keys a retry is always safe, so more retries cost nothing but time. Fewer retries means more failed charges for support to chase.

Which one should the backfill use? I'd go with the RFC, but then billing should change too, and nobody has said why it shipped with 3.
