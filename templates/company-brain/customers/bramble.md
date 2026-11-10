---
type: Customer
title: "Bramble & Co"
description: Home goods store that added an EU warehouse and joins the usage billing beta.
account: "/accounts/bramble.md"
owner: Ada Mensah
health: healthy
renewal_date: 2027-10-20
sources:
  - id: accounts-bramble
    resource: "/accounts/bramble.md"
    title: "Bramble & Co"
  - id: deals-mock-4
    resource: "/deals/mock-4.md"
    title: "Bramble & Co EU warehouse"
  - id: deals-mock-3
    resource: "/deals/mock-3.md"
    title: "Bramble & Co first contract"
  - id: meetings-mock-9
    resource: "/meetings/mock-9.md"
    title: "Bramble & Co usage billing beta call"
  - id: meetings-mock-4
    resource: "/meetings/mock-4.md"
    title: "Bramble & Co EU warehouse kickoff"
  - id: support-mock-10
    resource: "/support/mock-10.md"
    title: "Do you support Saturday delivery in the UK?"
  - id: support-mock-4
    resource: "/support/mock-4.md"
    title: "Can we ship from a second warehouse?"
  - id: issues-mock-12
    resource: "/issues/mock-12.md"
    title: Invoice lines per warehouse
generated:
  by: "workflow:update-customers:anthropic/claude-opus-5-5"
  at: "2026-11-05T16:00:00Z"
stale_after: "2026-12-05T16:00:00Z"
verified:
  - by: "process:crm-sync-check"
    at: "2026-11-06T02:00:00Z"
---

Bramble & Co is an online home goods store selling in the UK and the EU.[^accounts-bramble] It added a second warehouse in Rotterdam on 1 November, its volume is up about 30%, and it will join the usage-based billing beta if it starts on 1 December.[^deals-mock-4][^meetings-mock-9]

## Health

Healthy.

- The EU warehouse expansion closed on 20 October, and shipping from Rotterdam has run since 1 November.[^deals-mock-4][^meetings-mock-9]
- Both of its support questions were answered within the hour.[^support-mock-4][^support-mock-10]

## Deals

| Deal | Kind | Stage | Amount | Close date |
| --- | --- | --- | --- | --- |
| Bramble & Co EU warehouse[^deals-mock-4] | expansion | closed won | 28,000 USD | 20 October 2026 |
| Bramble & Co first contract[^deals-mock-3] | new | closed won | 42,000 USD | 10 March 2026 |

## What they've asked for

- Usage-based billing instead of the flat plan, since its volume is lumpy. Covered by [Usage-based billing](../projects/usage-based-billing.md).[^meetings-mock-4][^meetings-mock-9]
- Invoice lines per warehouse, since its finance team books them separately.[^issues-mock-12]
- Saturday delivery in the UK. Covered by [Saturday delivery](../projects/saturday-delivery.md).[^meetings-mock-4][^support-mock-10]

## Open issues

- ENG-256, Invoice lines per warehouse. Low priority, in the backlog.[^issues-mock-12]

## Support

2 threads in the last 90 days, both about shipments.

- 4 November: Do you support Saturday delivery in the UK?[^support-mock-10]
- 13 October: Can we ship from a second warehouse?[^support-mock-4]

## Recent conversations

- 5 November, usage billing beta call: Bramble joins the beta from 1 December, and asked for invoice lines per warehouse.[^meetings-mock-9]
- 16 October, EU warehouse kickoff: Rotterdam goes live on 1 November with a second sender address.[^meetings-mock-4]
