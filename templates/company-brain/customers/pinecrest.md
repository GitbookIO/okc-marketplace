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

Pinecrest Books is an independent bookseller with an online shop, shipping a few hundred parcels a week.[^accounts-pinecrest] It wants to move from the starter plan to usage-based billing, since its volume swings with the school year.[^deals-mock-10]

## Health

Healthy.

- On the starter plan since June, with one support question, answered within the hour.[^deals-mock-8][^support-mock-8]
- Its usage billing deal is qualified and waits for the product.[^deals-mock-10]

## Deals

| Deal | Kind | Stage | Amount | Close date |
| --- | --- | --- | --- | --- |
| Pinecrest Books usage billing[^deals-mock-10] | expansion | qualified to buy | 6,000 USD | 15 January 2027 |
| Pinecrest Books first contract[^deals-mock-8] | new | closed won | 9,000 USD | 2 June 2026 |

## What they've asked for

- Usage-based billing. Covered by [Usage-based billing](../projects/usage-based-billing.md).[^deals-mock-10]
- Invoices that show what each label cost.[^issues-mock-11]

## Open issues

- ENG-255, Invoice line items per label. Medium priority, to do.[^issues-mock-11]

## Support

1 thread in the last 90 days.

- 29 September: How long is a rate quote good for?[^support-mock-8]
