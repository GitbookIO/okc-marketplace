---
type: Meeting
title: "One-on-one: Maya and Nadia"
resource: "mock://meetings/1"
date: 2026-10-01
attendees: [Maya Chen, Nadia Petrov]
duration_minutes: 30
---

## Summary

- Maya leads the ledger migration, which moves billing history into the Ledger before usage-based billing starts on 1 December.
- Maya plans to run the backfill herself, since it's the riskiest step. Nadia asked her to think about who else could own it.
- Action: Maya sends Nadia the migration plan by 9 October.

## Transcript

**Nadia Petrov:** How is the migration scoped?

**Maya Chen:** Two years of credits, refunds and invoices move from the old billing tables into the Ledger, then invoices read from the Ledger. Cutover before the beta on 1 December.

**Nadia Petrov:** Who's doing what?

**Maya Chen:** Dev on dual writes. I'll take the backfill. It's the part that can go wrong in the most ways.

**Nadia Petrov:** That's exactly why I'd think twice. If the lead is heads down in the backfill, who's watching the whole migration?

**Maya Chen:** Fair. I'll think about it.

**Nadia Petrov:** Send me the plan when it's written.

**Maya Chen:** By the 9th.
