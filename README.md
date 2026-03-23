# Article Writer — Claude Code Skill (JO's Skill)

An AI-powered article writing system for product experts. Write authoritative articles about your company's product with deep research, your own writing style, and AI detection built in.

## Two commands

| Command | When | What it does |
|---------|------|-------------|
| `/article-setup` | Once | Builds your profile, product knowledge, writing style, and source library |
| `/article` | Every article | Loads all your knowledge and writes one great article |

**Why two?** Setup builds the knowledge base. Article writing uses it. Keeping them separate means `/article` gets 100% of its attention on YOUR article — no context wasted on setup questions.

## Features

- **Smart setup** — 6 questions, AI researches and pre-fills the rest
- **Deep product research** — maps every module, feature, edition, limit, and competitor
- **Your writing voice** — analyzes 5+ of your published articles to build a stylesheet
- **Thorough research** — 10–30 searches per article, cross-referenced, sourced
- **Product accuracy** — every claim verified against official docs
- **AI detection gate** — checks and humanizes until it passes

## Install

**Each company/product/voice needs its own project folder.** Different product? New folder. Different voice? New folder. Always copy from this repo, not from a filled-in project.

```bash
# 1. Create a folder
mkdir my-project && cd my-project

# 2. Copy from this repo
mkdir -p .claude/skills
cp -r /path/to/repo/article/ .claude/skills/
cp -r /path/to/repo/article-setup/ .claude/skills/
cp -r /path/to/repo/article-profiler/ .claude/skills/
cp -r /path/to/repo/product-learn/ .claude/skills/

# 3. Setup (once)
/article-setup

# 4. Write (every time)
/article "your topic here"
```

## How it works

```
/article-setup (once)
    │
    ├─ 6 questions — AI researches between each one
    ├─ Discovers and presents sources — you accept/reject each
    ├─ Builds deep product profile (every module, feature, edition, limit)
    ├─ Analyzes 5+ of your articles → builds your writing stylesheet
    └─ Readiness check — fills any gaps

/article "Flow Builder automation tips for admins" (every article)
    │
    ├─ Loads everything: profile, product, sources, stylesheet
    │
    ├─ Gathers intent — angle, audience, format, screenshots
    ├─ Researches the angle (10-30+ searches, full page fetches)
    ├─ Presents sources for you to double-check
    │
    ├─ Proposes outline → you approve
    ├─ Writes draft with verified product claims
    ├─ Applies your style (building blocks, vocabulary, voice)
    ├─ Product accuracy check
    ├─ AI detection → humanizes if needed
    │
    └─ Presents final article with sources
```

## All commands

| Command | What it does |
|---------|-------------|
| `/article-setup` | One-time onboarding — profile, product, style, sources |
| `/article` | Write an article — loads everything, researches, writes |
| `/article-profiler` | Rebuild style sheet from new samples (standalone) |
| `/product-learn` | Rebuild or update product profile (standalone) |

## Requirements

- [Claude Code CLI](https://docs.anthropic.com/en/docs/claude-code)
- Internet access (for research)

## License

MIT
