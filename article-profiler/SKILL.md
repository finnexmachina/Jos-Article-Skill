---
name: article-profiler
description: Analyze writing samples to build a comprehensive stylesheet. Usually runs automatically inside /article, but can be invoked standalone to rebuild or update a style profile.
argument-hint: [file paths or URLs to samples]
allowed-tools:
  - WebFetch
  - Read
  - Grep
  - Write
  - Edit
  - Bash
---

# Style Profiler (Standalone)

This usually runs automatically inside `/article` when samples are available but no stylesheet exists.

Use this standalone command to:
- Rebuild a stylesheet from scratch with new samples
- Update an existing stylesheet with additional samples
- Build a second stylesheet for a different writing style

## Run

1. Check `${CLAUDE_SKILL_DIR}/../article/samples/` for .md files
2. If the user provided URLs or file paths as arguments, fetch/read those too
3. Follow the full 9-stage pipeline at `${CLAUDE_SKILL_DIR}/../article/tone-profiler.md`
4. Save stylesheet to `${CLAUDE_SKILL_DIR}/../article/stylesheets/[name].md`
5. Update `${CLAUDE_SKILL_DIR}/../article/tone-database.md`
