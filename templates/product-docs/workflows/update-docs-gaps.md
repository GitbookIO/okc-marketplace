---
title: Update docs gaps
description: Turn support questions the docs don't answer into one gap page per question, with the threads that asked it and a count.
icon: message-question
on: support/**
commit: branch
files:
  '**': read-only
  gaps: read-write
  log.md: read-write
---

You keep `gaps/`: one page per question customers ask that the docs don't answer, so the writers fix the most asked first.

**Change only what's out of date.** If every file that triggered this run is already cited in `sources` on the pages you'd write, and those pages already say what it says, change nothing: write no file and add no line to `log.md`. That's what happens when this repo is created with all of Acme's example data, since the example records it ships with are already written up.

## For each support thread that triggered this run

1. Read its `## Question` and `## Answer`, and its `area`.
2. Read the docs that could answer it: reference pages in `docs/reference/`, guides in `docs/guides/` and entries in `docs/changelog/`. Pages with `status: draft` don't count, since readers can't see them yet.
3. If a page answers the question clearly, there's no gap. Count the thread as answered by the docs, and write nothing for it.
4. Otherwise, find the gap in `gaps/` that asks the same question, worded any way, in the same area. Add the thread to it. If none exists, create one.
5. If the matching gap has `state: resolved` and the page in `resolved_by` still answers the question, leave the gap resolved and only add the thread. If that page no longer answers it, set `state: open` and remove `resolved_by`.

For every gap you create or change, also read Pull Request records in `prs/`. If a merged pull request already shows the answer, like a limit or a behavior the docs never mention, cite it: the answer exists, it just isn't written down.

## What to write

`gaps/<slug>.md`, with the slug from the question, like `gaps/rate-quote-validity.md`.

Frontmatter:

- `type: Docs Gap`, `title` (the question, as a reader would ask it, ending in a question mark), `description` (one line on what's missing from the docs), `state` (`open`, or `resolved` as above), `area`.
- `threads`: bundle paths of every thread that asked it, oldest first. `thread_count`: how many.
- `sources`: every thread and pull request you cite, with `resource` as its bundle path, `title`, and `id` as `<folder>-<filename without .md>`, like `support-mock-4`.
- `generated`: the workflow signature you were given, with `at` set to now.
- Keep `resolved_by`, which Resolve gaps sets.

Body, in this order:

1. `## What customers ask`: one line per thread, oldest first, in the customer's words where you can, with a footnote.
2. `## What support answered`: what the answers had in common, and where they disagreed, with footnotes.
3. `## What the docs say`: link the pages that come closest and say what they leave out. If nothing comes close, say so.
4. `## Where the answer is`: pull requests that show the answer, with footnotes. Leave this section out if there are none.
5. If `thread_count` is 3 or more, a Vega-Lite bar chart in a `vega-lite` code block of threads per week, counted from each thread's `opened_at`.

Define no footnotes in the body. The `sources` ids are the labels.

## Index

## Log

If you changed any file, add one line to `log.md` under today's `## YYYY-MM-DD` heading (create it at the top if missing):
`- **Update** gaps from <n> threads: <n> new, <n> updated, <n> answered by the docs, by update-docs-gaps.`
