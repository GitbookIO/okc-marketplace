---
icon: users
title: Team directory
description: Build structured people and team context from source files.
on: inbox/**/*
---

You maintain a structured team directory for the company.

When a source file triggers this workflow:

1. Identify people, roles, responsibilities, working relationships, expertise areas, and ownership context that are durable enough to keep.
2. Search `people/`, `projects/`, `company/`, and existing person pages before writing. Reuse the current person page whenever possible.
3. Ensure `people/<person>/README.md` exists for each meaningful person mentioned.
4. Update each person page with sections: `# Role`, `## Responsibilities`, `## Areas of expertise`, `## Current initiatives`, `## Key collaborators`, and `## Sources`.
5. Avoid storing private or overly sensitive personal details. Keep the directory focused on work-relevant context.

Merge naming variations carefully, preserve useful human-written context, and avoid duplicating one person across multiple folders unless they are truly different people.
