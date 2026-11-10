---
type: Guide
title: Page through your shipments
description: Export every shipment with cursor pagination, without skipping any.
audience: Developers who sync shipments into another system
endpoints: [/docs/reference/list-shipments.md]
sources:
  - id: reference-list-shipments
    resource: /docs/reference/list-shipments.md
    title: List shipments
  - id: changelog-2026-10-22-cursor-pagination
    resource: /docs/changelog/2026-10-22-cursor-pagination.md
    title: Page through shipments with a cursor
  - id: gaps-list-shipments-page-size
    resource: /gaps/list-shipments-page-size.md
    title: What's the largest page size for list shipments?
generated:
  by: "workflow:update-guides:anthropic/claude-opus-5-5"
  at: "2026-10-22T18:00:00Z"
stale_after: "2026-11-21T18:00:00Z"
verified:
  - by: "human:lena@acme.example"
    at: "2026-10-23T09:30:00Z"
---

Exports and syncs need every shipment exactly once. This guide pages through your shipments with a cursor, so shipments created while you page are never skipped. It's for developers who sync shipments into another system.

1. **Ask for the first page.** Use the largest page, `limit=200`, to make as few requests as you can, and add any filters now.[^reference-list-shipments]

   ```bash
   curl https://api.acme.example/v1/shipments?limit=200&created_after=2026-10-01T00:00:00Z \
     -H "Authorization: Bearer $ACME_API_KEY"
   ```

2. **Follow the cursor.** Each page has `data` and `next_cursor`. Send `next_cursor` as `cursor` to get the next page, with the same filters.[^reference-list-shipments]

   ```bash
   curl https://api.acme.example/v1/shipments?limit=200&created_after=2026-10-01T00:00:00Z&cursor=c2hwXzhLZDI \
     -H "Authorization: Bearer $ACME_API_KEY"
   ```

3. **Stop at the end.** `next_cursor` is null on the last page.[^reference-list-shipments]

Don't change the filters halfway: a cursor sent with other filters returns `invalid_cursor`.[^reference-list-shipments] If you still page with `offset`, move to cursors. Offset pages stop at 100 shipments and can skip shipments created while an export runs, which is what customers ran into.[^changelog-2026-10-22-cursor-pagination][^gaps-list-shipments-page-size]

## Related

- [List shipments](../reference/list-shipments.md)
