---
type: Source
title: "Expand and contract migrations"
resource: "mock://sources/5"
kind: link
captured_at: "2026-10-07T20:15:00Z"
author: Maya Chen
---

## Summary

Saved a write-up of expand and contract migrations. It says dual writes before the backfill, re-runnable batches, compare before switching, contract last. That's the opposite order from what Dev proposed.

## Note

https://example.com/blog/expand-and-contract-migrations

Best write-up of the pattern I've found. What I'm taking:
- dual writes ON before the backfill. anything written mid-backfill lands in both places, so no gap, no catch-up
- backfill in batches you can re-run
- read from both and compare before switching
- contract last, after a quiet period

Which is the exact opposite of what Dev proposed yesterday: backfill first, then dual writes, then a catch-up run. Hm.
