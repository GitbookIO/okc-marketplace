---
type: Customer
title: Pinecrest Books
description: Small bookseller on the starter plan that wants usage-based billing.
account: "/accounts/pinecrest.md"
owner: Ada Mensah
health: healthy
renewal_date: 2027-06-02
sources:
  - id: accounts-pinecrest
    resource: "/accounts/pinecrest.md"
    title: Pinecrest Books
  - id: deals-mock-10
    resource: "/deals/mock-10.md"
    title: Pinecrest Books usage billing
  - id: deals-mock-8
    resource: "/deals/mock-8.md"
    title: Pinecrest Books first contract
  - id: support-mock-8
    resource: "/support/mock-8.md"
    title: "How long is a rate quote good for?"
  - id: issues-mock-11
    resource: "/issues/mock-11.md"
    title: Invoice line items per label
generated:
  by: "workflow:update-customers:anthropic/claude-opus-5-5"
  at: "2026-09-30T16:00:00Z"
stale_after: "2026-10-30T16:00:00Z"
---

[Pinecrest Books](../accounts/pinecrest.md) is an independent bookseller with an online shop, shipping a few hundred parcels a week. It wants to move from the starter plan to [usage-based billing](../deals/mock-10.md), since its volume swings with the school year.

## Health

Healthy.

- On the starter plan since June, under its [first contract](../deals/mock-8.md), with [one support question](../support/mock-8.md) answered within the hour.
- Its [usage billing deal](../deals/mock-10.md) is qualified and waits for the product.

## Deals

| Deal | Kind | Stage | Amount | Close date |
| --- | --- | --- | --- | --- |
| [Pinecrest Books usage billing](../deals/mock-10.md) | expansion | qualified to buy | 6,000 USD | 15 January 2027 |
| [Pinecrest Books first contract](../deals/mock-8.md) | new | closed won | 9,000 USD | 2 June 2026 |

## What they've asked for

- Usage-based billing, in its [usage billing deal](../deals/mock-10.md). Covered by [Usage-based billing](../projects/usage-based-billing.md).
- [Invoices that show what each label cost](../issues/mock-11.md).

## Open issues

- ENG-255, [Invoice line items per label](../issues/mock-11.md). Medium priority, to do.

## Support

1 thread in the last 90 days.

- 29 September: [How long is a rate quote good for?](../support/mock-8.md)
