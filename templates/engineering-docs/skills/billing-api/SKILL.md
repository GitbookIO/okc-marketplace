---
name: billing-api
description: How to change the Billing API safely. Use when working on charges, charge retries, idempotency keys or charge failure codes.
type: Skill
system: /systems/billing-api.md
sources:
  - id: systems-billing-api
    resource: /systems/billing-api.md
    title: "Billing API"
  - id: specs-mock-1
    resource: /specs/mock-1.md
    title: "Idempotent charges"
  - id: prs-mock-1
    resource: /prs/mock-1.md
    title: "Add idempotency keys to charge requests"
  - id: prs-mock-2
    resource: /prs/mock-2.md
    title: "Retry failed charges with a fixed delay"
  - id: prs-mock-16
    resource: /prs/mock-16.md
    title: "Store processor response codes on failed charges"
  - id: incidents-mock-1
    resource: /incidents/mock-1.md
    title: "Customers charged twice for one label"
  - id: runbooks-duplicate-charges
    resource: /runbooks/duplicate-charges.md
    title: "Duplicate charges"
generated:
  by: workflow:system-skills:anthropic/claude-opus-5-5
  at: 2026-11-09T07:00:00Z
---

## What it is

The [Billing API](../../systems/billing-api.md) charges customers for every label they buy and retries charges that fail. Label Service calls it on each purchase.

## Rules from specs

- Open drift: [Idempotent charges](../../specs/mock-1.md) requires at most 5 retries with exponential backoff from 2 seconds, but [retries now stop after 3, 10 seconds apart](../../prs/mock-2.md). Check with Payments before changing retry timing.
- Every charge request carries an [idempotency key](../../specs/mock-1.md) built from the label purchase ID.
- Every [retry reuses that key](../../specs/mock-1.md).
- The ledger [records one entry per key](../../specs/mock-1.md).

## How changes are made here

- [Charge logic](../../prs/mock-1.md) lives in `src/charges/`, and [retry behaviour](../../prs/mock-2.md) is tested in `test/charges/retry.test.ts`.
- [Schema changes](../../prs/mock-16.md) are numbered SQL files in `migrations/`.
- [Pull request descriptions](../../prs/mock-1.md) name the issue they fix and the spec they follow.

## Before you merge

- Run the retry tests with a processor timeout. A timeout is what [charged fourteen accounts twice](../../incidents/mock-1.md).
- Make sure the change can't [write a second ledger entry](../../runbooks/duplicate-charges.md) for one charge.
- If double charges show up after a deploy, [pause the charge retry job](../../runbooks/duplicate-charges.md) first.
