# Instructions for agents

This repo is {{ONE_LINE: what this repo holds}}. Workflows keep it current, and people review every change. These instructions are for agents connected over MCP or through the desktop app.

## Find your way

1. Read `index.md` first. There is no search, so it's the map: it lists every folder and what it holds.
2. List the folder you need. File names say what each page is about.

{{FOLDERS: one line per folder, saying what it holds and whether it's a record or a concept folder.}}

3. Check `types/` for the fields a type uses before you read or write its frontmatter.
4. Read `log.md` for what changed recently, newest first.

## Add material

- Put new material in `inbox/`, one file per item, as Markdown. Notes, transcripts, pasted documents and links all go there. Ingest inbox turns them into records, and the refinement workflows update the concept pages from those.
- Don't edit concept pages directly. They're owned by workflows, and a direct edit is overwritten or skipped on the next run. If a page is wrong, add the correction to `inbox/` and say which page it's about.
- Don't edit records. They mirror their source.
- Make every change on a branch, never on `main`. People review and merge it.

## Write well

- Frontmatter links are bundle paths, like `/systems/billing-api.md`.
- Keep the type's folder: one type per folder.
- Never invent names. Use the names already in the repo.
