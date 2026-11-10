---
type: Type
title: Meeting
icon: microphone
description: A meeting transcript or notes, one file per meeting.
schema:
  type: object
  properties:
    date:
      type: string
      format: date
      description: Day of the meeting.
    attendees:
      type: array
      description: Names of the people who attended.
      items:
        type: string
    account:
      type: string
      pattern: '^/accounts/[^/]+\.md$'
      description: Customer account the meeting was with.
    project:
      type: string
      pattern: '^/projects/[^/]+\.md$'
      description: Project the meeting was about.
    duration_minutes:
      type: integer
      description: Length in minutes.
      minimum: 0
  required: [date]
---

A meeting keeps the transcript or notes of one call. The body holds the summary first and the transcript after it.

- **Layer:** record. Written by ingest workflows, one file per source event. Refinements read records and never edit them.
- **Folder:** `meetings/`
- **Filenames:** `meetings/<source>-<id>.md`, like `meetings/granola-7c21.md`, or `meetings/upload-<date>-<slug>.md` for uploads. Mocks are `meetings/mock-<n>.md` with `resource: mock://meetings/<n>`.
- **Ingested from:** Fireflies, Granola, Gong, Otter, Fathom, or an upload.

Example frontmatter:

```yaml
type: Meeting
title: Billing API design review
resource: mock://meetings/4
date: 2026-11-03
attendees: [Lena Ito, Dev Okafor, Maya Chen]
```
