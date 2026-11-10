---
type: Customer
title: Tidewater Pharmacy
description: "Pharmacy chain evaluating Acme, waiting on Saturday delivery."
account: "/accounts/tidewater.md"
owner: Sam Reyes
sources:
  - id: accounts-tidewater
    resource: "/accounts/tidewater.md"
    title: Tidewater Pharmacy
  - id: deals-mock-7
    resource: "/deals/mock-7.md"
    title: Tidewater Pharmacy
  - id: meetings-mock-2
    resource: "/meetings/mock-2.md"
    title: Tidewater Pharmacy discovery call
  - id: issues-mock-8
    resource: "/issues/mock-8.md"
    title: "Saturday delivery: Parcelline weekend service levels in rates"
generated:
  by: "workflow:update-customers:anthropic/claude-opus-5-5"
  at: "2026-10-08T16:00:00Z"
stale_after: "2026-11-07T16:00:00Z"
status: draft
---

Tidewater Pharmacy is a pharmacy chain that sends prescriptions by post in three regions, and is evaluating Acme to replace its own carrier contracts.[^accounts-tidewater] It's a prospect. Its deal depends on Saturday delivery, since patients who order on a Friday can't wait until Monday.[^deals-mock-7][^meetings-mock-2]

## Deals

| Deal | Kind | Stage | Amount | Close date |
| --- | --- | --- | --- | --- |
| Tidewater Pharmacy[^deals-mock-7] | new | presentation scheduled | 120,000 USD | 31 December 2026 |

## What they've asked for

- Saturday delivery in all three regions, live in the first quarter, so it can sign by year end. Covered by [Saturday delivery](../projects/saturday-delivery.md).[^meetings-mock-2][^issues-mock-8]

## Open issues

- ENG-252, Saturday delivery: Parcelline weekend service levels in rates. High priority, to do.[^issues-mock-8]

## Recent conversations

- 7 October, discovery call: about 9,000 prescriptions a week across three regions. It would sign by year end if Saturday delivery is live in the first quarter, and doesn't need cold chain.[^meetings-mock-2]
