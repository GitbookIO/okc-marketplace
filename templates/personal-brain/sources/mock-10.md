---
type: Source
title: "Retries: the RFC and what shipped"
resource: "mock://sources/10"
kind: note
captured_at: "2026-10-24T11:20:00Z"
author: Maya Chen
---

## Summary

The RFC says a failed charge is retried 5 times with backoff, billing shipped 3 retries 10 seconds apart, and the backfill copied billing. With idempotency keys retries are safe either way. I'd go with the RFC, but nobody's said why billing shipped 3.

## Note

Retries. Still chewing on Tuesday's sync.

- Idempotent charges RFC: a failed charge gets retried 5x, exponential backoff from 2s
- what actually shipped in billing (per Dev): 3x, 10s apart. the backfill copied that.
- with idempotency keys a retry is always safe. more retries only cost time. fewer = more failed charges for support to chase.

So what should the backfill use? I'd go with the RFC, but then billing should change too, and nobody's said why it shipped with 3. Ask around.
