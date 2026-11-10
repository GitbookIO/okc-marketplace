---
type: Docs Gap
title: What's the largest page size for list shipments?
description: Customers exporting shipments couldn't find the page size limit, or a way to page without skipping shipments.
state: resolved
area: shipments
threads: [/support/mock-2.md, /support/mock-6.md]
thread_count: 2
resolved_by: /docs/reference/list-shipments.md
sources:
  - id: reference-list-shipments
    resource: /docs/reference/list-shipments.md
    title: List shipments
  - id: support-mock-2
    resource: /support/mock-2.md
    title: What's the largest page size for list shipments?
  - id: support-mock-6
    resource: /support/mock-6.md
    title: Offset pagination skips shipments during our export
generated:
  by: "workflow:resolve-gaps:anthropic/claude-opus-5-5"
  at: "2026-10-22T18:30:00Z"
---

## Resolved

[List shipments](../docs/reference/list-shipments.md) answers it since 22 October 2026: `limit` takes 1 to 200, and "Cursors don't skip shipments created while you page, which offset pages did."[^reference-list-shipments]

## What customers ask

- A nightly export asked for 500 per page, got a 400, and asked for the largest page size.[^support-mock-2]
- A team paging with `offset` found shipments skipped during their export, and asked for a safer way and bigger pages.[^support-mock-6]

## What support answered

The limit was 100 per page with `offset`, and cursor pagination with pages of up to 200 was coming.[^support-mock-2][^support-mock-6]

## What the docs say

List shipments listed `limit` and `offset` without a maximum, and didn't say that offset pages can skip shipments.
