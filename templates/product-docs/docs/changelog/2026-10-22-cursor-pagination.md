---
type: Changelog Entry
title: Page through shipments with a cursor
description: List shipments takes a cursor and pages of up to 200. offset is deprecated.
date: "2026-10-22"
api_version: "1.11.0"
change: changed
breaking: false
endpoints: [/docs/reference/list-shipments.md]
sources:
  - id: api-openapi
    resource: /api/openapi.yaml
    title: Acme Shipping API spec
  - id: prs-mock-2
    resource: /prs/mock-2.md
    title: Add cursor pagination to list shipments
generated:
  by: "workflow:sync-reference:anthropic/claude-opus-5-5"
  at: "2026-10-22T17:30:00Z"
---

List shipments takes `cursor` and returns `next_cursor`. Pages go up to 200 shipments, and the default stays at 50. Offset pages could skip shipments created during an export, and cursors don't.[^prs-mock-2]

## What to do

Nothing breaks: `offset` still works, up to 100 per page, but it's deprecated. Move to `cursor` with [List shipments](../reference/list-shipments.md).
