---
type: Meeting
title: "Ledger migration sync"
resource: "mock://meetings/6"
date: 2026-10-20
attendees: [Maya Chen, Dev Okafor]
project: "/projects/ledger-migration.md"
duration_minutes: 30
---

## Summary

- The Ledger accepts imported entries, marked `origin: legacy`. The expand step is done.
- Dev owns the backfill. A test run over two years of history on the staging copy took about three hours.
- Billing retries a failed charge 3 times, 10 seconds apart. The Idempotent charges RFC says 5 times with exponential backoff. The backfill's ledger writes need a policy too.

## Transcript

**Dev Okafor:** Imported entries work. They're marked origin legacy, so finance can tell them apart.

**Maya Chen:** Great, that's the expand step done. How long does the backfill take?

**Dev Okafor:** About three hours for two years, on the staging copy.

**Maya Chen:** And when a ledger write fails?

**Dev Okafor:** I copied what billing does for charges: three retries, ten seconds apart.

**Maya Chen:** The RFC says five, with exponential backoff.

**Dev Okafor:** Then billing doesn't match the RFC either. That's what shipped.

**Maya Chen:** Let's find out which one we actually want before the backfill runs.
