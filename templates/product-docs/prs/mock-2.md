---
type: Pull Request
title: Add cursor pagination to list shipments
resource: "mock://prs/2"
number: 548
repository: acme/shipments-api
state: merged
author: lena-ito
merged_at: "2026-10-22T16:00:00Z"
systems: [/systems/shipments-api.md]
---

List shipments takes a `cursor` and returns `next_cursor`. The default page size stays at 50, and the maximum goes from 100 to 200. Filters from the first request apply to every page, and a cursor sent with other filters returns `invalid_cursor`.

Offset pages skipped shipments when new ones were created during an export. `offset` still works, up to 100 per page, and is deprecated.

## Changed files

- `src/routes/shipments/list.ts`
- `src/pagination/cursor.ts`
