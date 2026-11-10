# Instructions for agents

This repo is Acme's public docs for its shipping API: a reference page per operation, task guides, a changelog, and the questions customers ask that the docs don't answer yet. Workflows keep it current from the API spec and support conversations, and people review every change. These instructions are for agents connected over MCP or through the desktop app.

## Find your way

1. Read `index.md` first. There is no search, so it's the map: it lists every folder and what it holds.
2. List the folder you need. File names say what each page is about.

   Concept folders, written by workflows:

   - `docs/reference/`: one page per API operation, with parameters, responses, errors and an example. Start here for questions about what the API does.
   - `docs/guides/`: task guides that walk through the API. Pages with `status: draft` aren't reviewed yet.
   - `docs/changelog/`: one entry per API change, named by date.
   - `gaps/`: questions customers ask that the docs don't answer yet, with the threads that asked them.
   - `digests/`: one summary per week.

   Record folders, one file per source event, linked from the concept pages that cite them:

   - `support/` and `prs/`.

   `api/openapi.yaml` is the API spec. People own it. Read it, and never change it unless a person asks you to.

   Concept pages cite their records in `sources`, and footnotes in the body point to them. Follow a footnote to check a claim.

3. Check `types/` for the fields a type uses before you read or write its frontmatter.
4. Read `log.md` for what changed recently, newest first.

## Add material

- Put new material in `inbox/`, one file per item, as Markdown. Support conversations and pull request descriptions go there. Ingest inbox turns them into records, and the refinement workflows update the concept pages from those.
- Don't edit concept pages directly. They're owned by workflows, and a direct edit is overwritten or skipped on the next run. If a page is wrong, add the correction to `inbox/` and say which page it's about.
- Don't edit records. They mirror their source.
- Make every change on a branch, never on `main`. People review and merge it.

## Write well

- Frontmatter links are bundle paths, like `/docs/reference/buy-label.md`.
- Keep the type's folder: one type per folder.
- Never invent names. Use the names already in the repo.
