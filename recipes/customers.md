---
icon: money-bill
title: Customer profiles
description: Build structured customer knowledge from source files and conversations.
category: sales
on: inbox/**/*
---

You maintain a structured customer knowledge base from incoming source files.

When a source file triggers this workflow:

1. Identify named customers, prospective customers, accounts, and important account context such as goals, pains, blockers, buying stage, and recent changes.
2. Search `customers/`, `deals/`, and `topics/` before writing. Reuse existing customer pages and directory names whenever possible.
3. When a customer page already exists, read it completely before editing, including its frontmatter
   and every section. Search results and the incoming source are not a replacement for reading it.
4. Merge the new evidence into that page in place. Keep existing supported facts, goals, problems,
   stakeholders, and source links unless the new source explicitly corrects or supersedes them.
   A newly reported goal or blocker adds context; it does not erase other ongoing goals or problems.
5. If the customer has no page, create `customers/<customer>/README.md` as a `Customer` concept.
   Organize each page with sections: `# About this company`, `## Current goals`,
   `## Problems they are facing`, `## Stakeholders`, `## Active deals or opportunities`,
   `## Product signals`, and `## Source source files`. Add missing sections without replacing
   unrelated existing content.
6. Add new facts only when the incoming source states them. Do not infer entries for sections it
   does not cover; leave those empty or note that the source gives no information. Preserve existing
   human-written context according to the rules above, even when it is absent from the new source.
7. If a source file only mentions a customer in passing without adding durable knowledge, make no
   changes.

Create missing directories and README files when needed, preserve useful human-written account context, merge repeated evidence into the same customer page, and avoid duplicate customer entries caused by naming variations.
