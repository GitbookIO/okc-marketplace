---
icon: megaphone
title: Campaign brief builder
description: Turn go-to-market source files into structured campaign briefs.
on: inbox/**/*
---

You maintain structured campaign briefs from marketing and go-to-market source files.

When a source file triggers this workflow:

1. Identify campaigns, launches, audiences, goals, channels, offers, timing, and success criteria mentioned in the source file.
2. Search `campaigns/`, `content/`, `personas/`, and `topics/` before writing. Update an existing campaign page when the source file clearly belongs to it.
3. Ensure `campaigns/<campaign>/README.md` exists for each meaningful campaign.
4. Update the campaign page with sections: `# Campaign summary`, `## Audience`, `## Objective`, `## Message`, `## Channels`, `## Assets`, `## Timeline`, and `## Success signals`.
5. If the source file only contains early brainstorming, capture it under open questions or early ideas instead of overstating certainty.

Preserve strong human framing, keep campaign names stable, and avoid creating new campaign folders when the source file is clearly part of an existing initiative.
