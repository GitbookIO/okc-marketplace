---
type: Source
title: "Expand and contract migrations"
resource: "mock://sources/5"
kind: link
captured_at: "2026-10-07T20:15:00Z"
author: Maya Chen
---

## Summary

Notes on a write-up of expand and contract migrations: turn on dual writes before the backfill so there's no gap, backfill in batches you can re-run, compare before switching, contract last. That's the opposite order from Dev's proposal.

## Note

https://example.com/blog/expand-and-contract-migrations

Good write-up of the pattern. What I took from it:
- Turn on dual writes before the backfill. Anything written during the backfill lands in both places, so there's no gap to catch up.
- Backfill in batches you can re-run.
- Read from both and compare before you switch.
- Contract last, after a quiet period.

That's the opposite of what Dev proposed yesterday: backfill first, then dual writes, then a catch-up run.
