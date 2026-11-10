---
type: Source
title: "Metering: what counts as a label bought"
resource: "mock://sources/13"
kind: note
captured_at: "2026-11-06T16:40:00Z"
author: Maya Chen
---

## Summary

What metering counts: a label when it's bought, minus labels voided within 24 hours. Owen wants every invoice to close at midnight UTC, Bramble closes its month on Amsterdam time. Maya told Owen the beta's first invoices come with a CSV.

## Note

Notes on metering after the Bramble call yesterday.

- Dev's metering counts a label when it's bought.
- A label voided within 24 hours isn't billed. So the count can go down after the fact, and the usage page has to show that.
- The month boundary: Owen wants every invoice to close at midnight UTC, the same for every customer. Felix Grant at Bramble said their finance team closes the month on Amsterdam time. A label bought at 00:30 on 1 December in Rotterdam is November for us and December for them.
- Told Owen on Monday that the beta's first invoices come with a CSV of labels bought. He's fine with it.

Open: do we show both, or tell beta customers it's UTC?
