---
type: Customer
title: Northline Freight
description: Enterprise carrier whose two-year renewal waits on 30 days of webhook delivery history.
account: "/accounts/northline.md"
owner: Sam Reyes
health: watch
renewal_date: 2026-12-15
sources:
  - id: accounts-northline
    resource: "/accounts/northline.md"
    title: Northline Freight
  - id: deals-mock-2
    resource: "/deals/mock-2.md"
    title: Northline Freight 2027 renewal
  - id: deals-mock-1
    resource: "/deals/mock-1.md"
    title: Northline Freight 2026 renewal
  - id: meetings-mock-8
    resource: "/meetings/mock-8.md"
    title: Northline Freight renewal check-in
  - id: support-mock-11
    resource: "/support/mock-11.md"
    title: We need more than 7 days of webhook history
  - id: support-mock-7
    resource: "/support/mock-7.md"
    title: "How far back does the delivery log go?"
  - id: support-mock-3
    resource: "/support/mock-3.md"
    title: Tracking webhooks arrive out of order
  - id: issues-mock-7
    resource: "/issues/mock-7.md"
    title: "Delivery log: keep 30 days of attempts"
generated:
  by: "workflow:update-customers:anthropic/claude-opus-5-5"
  at: "2026-11-06T16:00:00Z"
stale_after: "2026-12-06T16:00:00Z"
verified:
  - by: "human:sam@acme.example"
    at: "2026-11-06T17:30:00Z"
---

[Northline Freight](../accounts/northline.md) is a regional freight and parcel carrier that buys about 40,000 labels a week through Acme and listens to tracking webhooks for every one. It has renewed once, and its [two-year renewal](../deals/mock-2.md) now waits on one thing: 30 days of webhook delivery history for its auditors.

## Health

Watch.

- The 186,000 USD [renewal](../deals/mock-2.md) closes on 15 December, and Northline won't sign without a date for 30 days of delivery history, as the [renewal check-in](../meetings/mock-8.md) made clear.
- [We need more than 7 days of webhook history](../support/mock-11.md): its auditors check every missed tracking event against a month of records, and the delivery log keeps 7 days.
- At the [renewal check-in](../meetings/mock-8.md), Acme promised a date on a follow-up call on 9 November.

## Deals

| Deal | Kind | Stage | Amount | Close date |
| --- | --- | --- | --- | --- |
| [Northline Freight 2027 renewal](../deals/mock-2.md) | renewal | negotiation | 186,000 USD | 15 December 2026 |
| [Northline Freight 2026 renewal](../deals/mock-1.md) | renewal | closed won | 168,000 USD | 15 December 2025 |

## What they've asked for

- [30 days of webhook delivery history](../issues/mock-7.md), so its auditors can look back a month. Asked about in [We need more than 7 days of webhook history](../support/mock-11.md) and [How far back does the delivery log go?](../support/mock-7.md). Covered by [Webhook delivery log](../projects/webhook-delivery-log.md).
- Tracking events for one shipment [in order](../support/mock-3.md). Support suggested sorting by `occurred_at` until delivery was partitioned, which has [since shipped](../meetings/mock-8.md).

## Open issues

- ENG-251, [Delivery log: keep 30 days of attempts](../issues/mock-7.md). High priority, in the backlog.

## Support

3 threads in the last 90 days, all about webhooks.

- 5 November: [We need more than 7 days of webhook history](../support/mock-11.md).
- 22 October: [How far back does the delivery log go?](../support/mock-7.md)
- 9 October: [Tracking webhooks arrive out of order](../support/mock-3.md).

## Recent conversations

- 3 November, [renewal check-in](../meetings/mock-8.md): Northline needs a date for 30 days of delivery history before it signs. Acme comes back with one on 9 November.
