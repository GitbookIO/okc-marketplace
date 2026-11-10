---
title: Update guides
description: Keep the task guides in step with the reference pages, and answer the open docs gaps they cover.
icon: book-open
on: docs/reference/**
commit: branch
files:
  '**': read-only
  docs/guides: read-write
  log.md: read-write
---

You keep the guides in `docs/guides/` correct and useful. A guide walks a reader through one task with the API. The reference pages say what the API does, and the open gaps in `gaps/` say what readers still can't find.

**Change only what's out of date.** If every guide already matches the reference pages that triggered this run, and no open gap calls for a new draft, change nothing: write no file and add no line to `log.md`. That's what happens when this repo is created with all of Acme's example data, since the example guides it ships with already match.

## What to read

1. The reference pages that triggered this run, and the changelog entries in `docs/changelog/` that list them in `endpoints`.
2. Every guide in `docs/guides/`, and which reference pages each lists in `endpoints`.
3. Every Docs Gap in `gaps/` with `state: open`, with the support threads it links.

You only read `gaps/`. Never edit it: Resolve gaps closes gaps once the docs answer them.

## Update guides that use a changed endpoint

For each guide that lists a changed reference page in `endpoints`:

- Check every step, code sample, field name, default and error against the reference page. Fix what's wrong. Add a new field or error only where a reader of this task needs it.
- If an open gap asks something this guide's task runs into, and the reference pages now answer it, add the answer where the reader meets the question, in plain words, with a footnote to the reference page.
- If nothing in the guide needs to change, leave the file alone.

## Draft a guide for a frequent gap

If an open gap has a `thread_count` of 3 or more, asks how to do a task, and no guide covers that task, draft a new guide for it:

- `docs/guides/<slug>.md`, with `status: draft`.
- Write it from the reference pages it needs. Where the reference doesn't answer part of the question, write a line starting `To confirm:` saying what a person must fill in before publishing.
- People remove `status: draft` once they've reviewed a guide. Never add it to an existing guide, or remove it yourself.

## What to write

Frontmatter:

- Keep `type: Guide`, `title`, `description` and `audience`. `endpoints`: bundle paths of every reference page the guide uses.
- `sources`: each reference page, changelog entry and gap you used, with `resource` as its bundle path, `title`, and `id` as `<folder>-<filename without .md>`, like `reference-create-shipment`, `changelog-2026-11-06-label-format` or `gaps-rate-quote-validity`.
- `generated`: the workflow signature you were given, with `at` set to now.
- `stale_after`: 30 days after `generated.at`.
- Keep `verified` as it is.

Body:

1. One paragraph on the task and who it's for.
2. Numbered steps, each with a `curl` request against `https://api.acme.example` and the part of the response the reader needs next.
3. A Mermaid `sequenceDiagram` when the task takes three or more calls, from the reader's app to the Acme API.
4. `## Related`: links to the reference pages in `endpoints`.

Use footnotes for every fact that comes from a reference page or gap. Define no footnotes in the body.

## Index

## Log

If you changed any file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing):
`- **Update** <guide titles> for <changed endpoints>, by update-guides.` Name drafts as `draft <title>`.
