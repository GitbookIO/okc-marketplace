---
type: Customer
title: Harbor Coffee Roasters
description: "Coffee subscription roaster, refunded after duplicate charges and now using the delivery log."
account: "/accounts/harbor.md"
owner: Ada Mensah
health: healthy
renewal_date: 2027-04-15
sources:
  - id: accounts-harbor
    resource: "/accounts/harbor.md"
    title: Harbor Coffee Roasters
  - id: deals-mock-9
    resource: "/deals/mock-9.md"
    title: Harbor Coffee Roasters first contract
  - id: support-mock-9
    resource: "/support/mock-9.md"
    title: Webhook for shipped orders never arrived
  - id: support-mock-1
    resource: "/support/mock-1.md"
    title: We were charged twice for the same label
  - id: meetings-mock-7
    resource: "/meetings/mock-7.md"
    title: Harbor Coffee Roasters check-in
  - id: issues-mock-6
    resource: "/issues/mock-6.md"
    title: "Delivery log: export attempts as CSV"
  - id: issues-mock-1
    resource: "/issues/mock-1.md"
    title: Refund duplicate label charges
generated:
  by: "workflow:update-customers:anthropic/claude-opus-5-5"
  at: "2026-11-02T16:00:00Z"
stale_after: "2026-12-02T16:00:00Z"
---

[Harbor Coffee Roasters](../accounts/harbor.md) is a coffee roaster with a subscription service that marks orders shipped when Acme's tracking webhook arrives. It was [charged twice for labels](../support/mock-1.md) on 2 October and refunded, and now uses the webhook delivery log to find and resend [missed events](../support/mock-9.md).

## Health

Healthy.

- The [refunds for the duplicate charges](../issues/mock-1.md) all arrived, as noted at the [check-in](../meetings/mock-7.md).
- When [three shipped events went missing on 2 November](../support/mock-9.md), the delivery log showed why, and Harbor resent them itself.

## Deals

| Deal | Kind | Stage | Amount | Close date |
| --- | --- | --- | --- | --- |
| [Harbor Coffee Roasters first contract](../deals/mock-9.md) | new | closed won | 31,000 USD | 15 April 2026 |

## What they've asked for

- A history of webhook deliveries, to tell whether Acme sent an event, as Harbor asked at its [check-in](../meetings/mock-7.md). Covered by [Webhook delivery log](../projects/webhook-delivery-log.md).
- [Exporting delivery attempts as CSV](../issues/mock-6.md), since its support team works from spreadsheets, as Harbor asked at its [check-in](../meetings/mock-7.md).

## Open issues

- ENG-250, [Delivery log: export attempts as CSV](../issues/mock-6.md). Low priority, in the backlog.

## Support

2 threads in the last 90 days.

- 2 November: [Webhook for shipped orders never arrived](../support/mock-9.md).
- 2 October: [We were charged twice for the same label](../support/mock-1.md).

## Recent conversations

- 28 October, [check-in](../meetings/mock-7.md): refunds arrived. Harbor asked to export the delivery log, which launched with 7 days of history on 30 October.
