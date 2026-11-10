---
type: Source
title: "Usage API: first design notes"
resource: "mock://sources/3"
kind: note
captured_at: "2026-10-01T12:30:00Z"
author: Maya Chen
---

## Summary

First pass at a usage endpoint: GET /v1/usage by month, the same cursor pagination as list shipments, integer amounts in minor units, a beta flag per account, docs before code. Still unsure how voided labels show up.

## Note

Usage API, first pass. Customers want to see labels bought before the invoice shows up.

- `GET /v1/usage`, by month: labels bought, amount for each
- cursor pagination, same as list shipments, max 200 a page. do NOT invent a second style
- amounts: integers, minor units, with a currency. never floats. never.
- beta flag per account until 1 Dec
- docs page first, then code. can't explain a field in one sentence → wrong field

?? voided label: negative amount, or just gone?
