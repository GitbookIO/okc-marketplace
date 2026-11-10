---
type: Pull Request
title: Let callers choose the label format
resource: "mock://prs/8"
number: 101
repository: acme/label-service
state: merged
author: ravi-menon
merged_at: "2026-11-06T11:15:00Z"
systems: [/systems/label-service.md]
---

Buy a label takes `label_format`: `pdf_4x6`, the default and what every label used until now, `pdf_a4`, or `zpl` for thermal printers. The label response says which format the file is in.

## Changed files

- `src/routes/labels/buy.ts`
- `src/render/formats.ts`
