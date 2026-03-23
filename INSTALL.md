# Article Writing Skill — Install

## Important: One folder per identity

Each company/product/voice gets its own project folder. Different product? New folder. Different voice? New folder.

**Always copy from this repo, not from a previous project.**

## Setup a new project

```bash
# 1. Create a folder
mkdir my-project && cd my-project

# 2. Copy from this repo
mkdir -p .claude/skills
cp -r /path/to/repo/article/ .claude/skills/
cp -r /path/to/repo/article-setup/ .claude/skills/
cp -r /path/to/repo/article-profiler/ .claude/skills/
cp -r /path/to/repo/product-learn/ .claude/skills/

# 3. Setup (once — ~10 minutes)
/article-setup

# 4. Write articles
/article "your topic"
```

## Commands

| Command | When | What it does |
|---------|------|-------------|
| `/article-setup` | Once per folder | Builds profile, product knowledge, style, sources |
| `/article` | Every article | Loads everything, researches, writes |
| `/article-profiler` | Anytime | Rebuild style sheet from new samples |
| `/product-learn` | Anytime | Rebuild or update product profile |

## Have ready

- **5+ published articles** (URLs to paste during setup) — for your writing style profile
- **Product screenshots** — paste per article when relevant

## Requirements

- Claude Code CLI
- Internet access
