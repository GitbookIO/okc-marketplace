---
type: Project
title: "Usage-based billing"
description: "Charge per label bought instead of a flat volume tier, starting with a beta on 1 December."
state: active
lead: Maya Chen
target_date: 2026-12-01
sources:
  - id: sources-mock-3
    resource: "/sources/mock-3.md"
    title: "Usage API: first design notes"
  - id: meetings-mock-4
    resource: "/meetings/mock-4.md"
    title: "Usage billing pricing review"
  - id: meetings-mock-9
    resource: "/meetings/mock-9.md"
    title: "Bramble & Co usage billing beta call"
  - id: sources-mock-13
    resource: "/sources/mock-13.md"
    title: "Metering: what counts as a label bought"
generated:
  by: "workflow:update-projects:anthropic/claude-opus-5-5"
  at: "2026-11-06T17:20:00Z"
stale_after: "2026-12-06T17:20:00Z"
verified:
  - by: "process:linear-sync-check"
    at: "2026-11-07T06:00:00Z"
---

You're leading the switch to charging per label bought instead of a flat volume tier, with rate quotes free.[^meetings-mock-4] The beta starts on 1 December, and Bramble & Co is in.[^meetings-mock-9] The first invoices come with a CSV of labels bought.[^sources-mock-13]

## Where it stands

- Pricing is agreed: per label bought, quotes free.[^meetings-mock-4]
- Metering counts a label when it's bought, minus voids within 24 hours.[^sources-mock-13]
- The usage endpoint is designed, behind a beta flag per account.[^sources-mock-3]
- Bramble joins if the beta starts on 1 December. Its volume is up about 30% since the Rotterdam warehouse opened.[^meetings-mock-9]

## Next steps

- Ada checks how invoices handle a customer whose month closes on Amsterdam time, before the beta.[^meetings-mock-9]
- Add invoice lines per warehouse to your list for after the first version.[^meetings-mock-9]

## Decisions

- By 6 November: the beta's first invoices come with a CSV of every label bought.[^sources-mock-13]
- 14 October: per label bought, quotes stay free. A free tier gets its own meeting.[^meetings-mock-4]

## Risks

- Invoices close at midnight UTC, but Bramble closes its month on Amsterdam time.[^meetings-mock-9][^sources-mock-13]
