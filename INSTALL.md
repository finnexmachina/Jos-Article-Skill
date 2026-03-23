# Article Writing Skill — Install

## Important: One folder per identity

Each company/product/voice gets its own project folder. The skill builds a complete profile — product knowledge, writing style, research sources, screenshots — all tied to one identity.

**Different product? New folder. Different voice? New folder.**

```
~/projects/
├── salesforce-blog/        ← writing about Salesforce for the company blog
├── hubspot-content/        ← writing about HubSpot for a client
└── consulting-articles/    ← writing as an independent consultant
```

## Setup a new project

**Always copy from the original repo, not from a previous project.** A filled-in project has your old profile data in the files — you want clean templates for a fresh start.

```bash
# 1. Create a folder
mkdir my-project && cd my-project

# 2. Copy from the ORIGINAL repo (not a previous project)
mkdir -p .claude/skills
cp -r /path/to/repo/article/ .claude/skills/
cp -r /path/to/repo/article-profiler/ .claude/skills/
cp -r /path/to/repo/product-learn/ .claude/skills/

# 3. Run it
/article
```

If you already set up a project and want another identity, always go back to the original download/clone for a fresh copy.

## First run

The skill will:
1. Ask 5 questions (name, company, product, audience, style)
2. Research your company and product automatically
3. Show what it found — you confirm or correct
4. Build a deep product profile
5. You're writing

## Commands

| Command | What it does |
|---------|-------------|
| `/article` | Everything — setup, research, write, detect |
| `/article-profiler` | Rebuild style sheet from new samples (standalone) |
| `/product-learn` | Rebuild or update product profile (standalone) |

## Optional prep

These make the first article better but aren't required:

- **Writing samples** — 5+ articles in your voice (URLs to paste when asked)
- **Product screenshots** — a few screenshots of the features you'll write about

## Requirements

- Claude Code CLI
- Internet access (for research)
