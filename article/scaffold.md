# Auto-Scaffold

Creates the workspace. Runs silently on first `/article` call.

---

## Step 1 — Create directories

```bash
mkdir -p "${CLAUDE_SKILL_DIR}/samples"
mkdir -p "${CLAUDE_SKILL_DIR}/stylesheets"
mkdir -p "${CLAUDE_SKILL_DIR}/products"
mkdir -p "${CLAUDE_SKILL_DIR}/screenshots"
```

## Step 2 — Create files (only if they don't exist)

**Never overwrite existing files.**

### knowledge-base.md

```markdown
# Knowledge Base
<!-- Auto-filled via /article conversation. Structure below. -->

## Author
## Company
## Product
## Product Positioning
## Audience
## Publication
## Standing Instructions
- Never use placeholder text in the final draft
- Always fact-check product claims against official docs
```

### research-profile.md

```markdown
# Research Profile
<!-- Auto-filled via /article conversation. Structure below. -->

## Product Sources
## Competitor Sources
## General Sources
### Tier 1
### Tier 2
### Blacklisted

## Standing Research Rules
- Cross-reference key claims across 2+ sources
- Verify product claims against official docs
- Note edition/tier availability
- Flag anything older than 6 months
- Verify competitive claims from competitor's own materials
```

### product-angles.md

```markdown
# Product Angles
<!-- Grows over time. Added during setup and suggested after each article. -->
```

### tone-database.md

```markdown
# Style Profiles
<!-- Auto-updated when style profiler runs. -->
```

### SETUP.md

```markdown
# Article Skill

Two commands:
1. `/article-setup` — run once to build your profile, product knowledge, and writing style
2. `/article` — run every time to write an article

One folder = one identity. Different company or voice? New folder, fresh copy from the repo.
```

---

## Step 3 — Confirm

```bash
ls "${CLAUDE_SKILL_DIR}/samples/" "${CLAUDE_SKILL_DIR}/stylesheets/" "${CLAUDE_SKILL_DIR}/products/" "${CLAUDE_SKILL_DIR}/screenshots/" "${CLAUDE_SKILL_DIR}/knowledge-base.md" "${CLAUDE_SKILL_DIR}/research-profile.md" "${CLAUDE_SKILL_DIR}/tone-database.md" "${CLAUDE_SKILL_DIR}/product-angles.md" 2>/dev/null
```

All present → done.
