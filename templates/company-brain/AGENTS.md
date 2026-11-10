# Instructions for agents

This repo is Acme's company brain: what the company knows about its customers, projects and decisions, joined from meetings, support conversations, the CRM, the issue tracker and Slack. Workflows keep it current, and people review every change. These instructions are for agents connected over MCP or through the desktop app.

## Find your way

1. Read `index.md` first. There is no search, so it's the map: it lists every folder and what it holds.
2. List the folder you need. File names say what each page is about.

   Concept folders, written by workflows:

   - `customers/`: one page per customer, with its health, deals, requests, open issues and recent conversations. Start here for questions about a customer.
   - `projects/`: one page per project, with its progress, who it's for and its risks.
   - `decisions/`: one page per decision, with the options, the reasons and who decided. Start here for "why did we".
   - `teams/`: one page per team, with its projects, its customers and the pages it needs to review.
   - `digests/`: one summary per week.

   Pages with `status: draft` aren't reviewed yet. Pages past their `stale_after` date may be out of date.

   Record folders, one file per source event, linked from the concept pages that cite them:

   - `accounts/`, `deals/`, `meetings/`, `support/`, `issues/` and `discussions/`.

   Concept pages cite their records in `sources`, and footnotes in the body point to them. Follow a footnote to check a claim, or read the meeting or thread itself for the exact words.

   There are no pages about individual people. Names appear only as the records give them.

3. Check `types/` for the fields a type uses before you read or write its frontmatter.
4. Read `log.md` for what changed recently, newest first.

## Add material

- Put new material in `inbox/`, one file per item, as Markdown. Meeting notes, call transcripts and pasted chat threads go there. Ingest inbox turns them into records, and the refinement workflows update the concept pages from those.
- Don't edit concept pages directly. They're owned by workflows, and a direct edit is overwritten or skipped on the next run. If a page is wrong, add the correction to `inbox/` and say which page it's about.
- Don't edit records. They mirror their source.
- Make every change on a branch, never on `main`. People review and merge it.

## Write well

- Frontmatter links are bundle paths, like `/accounts/northline.md`.
- Keep the type's folder: one type per folder.
- Never invent names. Use the names already in the repo.
