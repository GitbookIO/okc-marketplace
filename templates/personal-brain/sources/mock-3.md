---
type: Source
title: "Usage API: first design notes"
resource: "mock://sources/3"
kind: note
captured_at: "2026-10-01T12:30:00Z"
author: Maya Chen
---

## Summary

First design for a usage endpoint: GET /v1/usage by month, cursor pagination like list shipments, amounts as integers in minor units, behind a beta flag per account, with the docs page written before the code. Open: how voided labels show up.

## Note

Usage API, first pass. Customers need to see labels bought before the invoice arrives.

- `GET /v1/usage`, filtered by month, listing labels bought with the amount for each.
- Cursor pagination, the same as list shipments, pages of up to 200. Don't invent a second style.
- Amounts in minor units, as integers, with a currency. Never floats.
- Behind a beta flag per account until 1 December.
- Write the docs page before the code. If I can't explain a field in one sentence, it's the wrong field.

Open: does a voided label show up with a negative amount, or disappear?
