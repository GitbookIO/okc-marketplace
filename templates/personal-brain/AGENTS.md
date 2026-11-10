# Instructions for agents

This repo is one person's personal brain: their own notes and meetings, compiled by workflows into topic, project and person pages. It belongs to the person named at the top of `index.md`. You're reading it over MCP or through the desktop app, and you can help them add to it, but you never write the compiled pages yourself. Workflows do, and the person reviews every change.

## The one rule

**Write new material to `inbox/`. Never edit a page in `topics/`, `people/` or `projects/`.**

Those pages are compiled from the records. A direct edit skips the record it should come from, so the page cites nothing for it, and the next workflow run either overwrites it or leaves it unexplained. If the person tells you something new, or a page is wrong, save it to `inbox/` instead, and the workflows fold it in on a branch the person reviews.

Don't edit `sources/` or `meetings/` either. They're records of what was captured, and pages cite them.

## Find your way

1. Read `index.md` first. There is no search, so it's the map. Its Pages section lists every topic, project and person page with one line on each.
2. Open the page you need. To answer a question, start from the topic page, then follow its footnotes to the sources and meetings behind each claim.
3. Folders:
   - `topics/`: one page per subject, with the current understanding, a Contradictions section where notes disagree, and open questions. Concept folder, written by Update topics.
   - `projects/`: one page per piece of work with a goal and an end, at work or not. Concept folder, written by Update projects.
   - `people/`: one page per person who comes up in two or more records. Concept folder, written by Update people. There's no page about the owner.
   - `digests/`: one weekly review per week, with what was captured and the open threads. Concept folder, written by Weekly review.
   - `sources/`: one record per item that came through the inbox. Record folder.
   - `meetings/`: one record per meeting, from Granola, Fireflies or the inbox. Record folder.
4. Pages with `status: draft` aren't reviewed yet. Pages past their `stale_after` date may be out of date. When notes disagree, say so and quote both sides from the Contradictions section, rather than picking one.
5. Check `types/` for the fields a type uses, and `log.md` for what changed recently, newest first.

## Save what you discussed

When the person asks you to save or remember something, like a summary of your conversation:

1. Make a branch, never `main`.
2. Add one file to `inbox/`, named `inbox/<YYYY-MM-DD>-<slug>.md`, like `inbox/2026-11-09-ledger-backfill-order.md`. One file per item.
3. Write it as plain Markdown, no frontmatter:
   - a first line saying what it is, who it was with and the date, like `Conversation with Claude about the ledger backfill, 9 November 2026`
   - what was concluded, in the person's words where you can, one point per line
   - what's still open, and anything someone agreed to do, with who and when
   - names and project titles spelled the way `people/` and `projects/` spell them, and nothing you made up
4. Tell the person the branch name, so they can merge it.

Ingest inbox turns the file into a record in `sources/` on that branch. Once the person merges it, Update topics, Update projects and Update people each open a branch with the pages that changed.

## Write well

- Keep their words. A summary that says what was decided, and why, is worth more than a transcript.
- Save corrections the same way: say which page is wrong, what it should say, and why.
- Never invent names, dates or claims.
