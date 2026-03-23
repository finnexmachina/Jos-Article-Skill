# Article Writer — Claude Code Skill (JO's Skill)

An AI-powered article writing system for product experts. Write authoritative articles about your company's product with deep research, your own writing style, and AI detection built in.

## What it does

One command: `/article`

- **Smart setup** — 5 questions, AI researches and pre-fills the rest
- **Deep product research** — maps every module, feature, edition, limit, and competitor
- **Your writing voice** — analyzes your published writing and builds a reusable stylesheet
- **Thorough research** — 10–30 searches per article, cross-referenced, sourced
- **Product accuracy** — every claim verified against official docs
- **AI detection gate** — checks against GPTZero, ZeroGPT, etc. and humanizes until it passes

## Install

**Each company/product/voice needs its own project folder.** The skill builds a complete profile — product knowledge, writing style, research sources, screenshots — all tied to one identity. To write for a different company, product, or voice, create a new folder and copy the skill fresh from this repo.

```
~/projects/
├── salesforce-blog/        ← Jo writing about Salesforce
│   └── .claude/skills/     ← copy skill here, run /article
├── hubspot-content/        ← Same Jo, different product
│   └── .claude/skills/     ← fresh copy, fresh setup
└── consulting-articles/    ← Different voice entirely
    └── .claude/skills/     ← fresh copy, fresh setup
```

### Setup a new project

```bash
# 1. Create a folder for this company/product/voice
mkdir my-project && cd my-project

# 2. Copy the skill in
mkdir -p .claude/skills
cp -r /path/to/article/ .claude/skills/
cp -r /path/to/article-profiler/ .claude/skills/
cp -r /path/to/product-learn/ .claude/skills/

# 3. Run it
/article
```

First run asks 5 questions, researches the rest, and you're writing.

**One folder = one identity.** Different product? New folder. Different audience? New folder. Different writing voice? New folder.

## Commands

| Command | What it does |
|---------|-------------|
| `/article` | Everything — setup, research, write, detect |
| `/article-profiler` | Rebuild style sheet from new samples (standalone) |
| `/product-learn` | Rebuild or update product profile (standalone) |

## Optional inputs

| Input | How to provide |
|-------|---------------|
| Writing samples | Paste URLs or text when asked during setup |
| Product screenshots | Attach with your article request |

## How it works

```
/article "Flow Builder automation tips for admins"
    │
    ├─ Loads your profile (author, company, product positioning)
    ├─ Loads product profile (features, editions, limits, competitors)
    ├─ Loads your stylesheet (voice, structure, vocabulary)
    │
    ├─ Researches the specific angle (10-30 searches + page fetches)
    ├─ Reads any screenshots you attached
    │
    ├─ Proposes outline → you approve
    ├─ Writes draft with verified product claims
    ├─ Applies your style in 6 passes
    ├─ Checks product accuracy
    ├─ Runs AI detection → humanizes if needed
    │
    └─ Presents final article with sources
```

## Requirements

- [Claude Code CLI](https://docs.anthropic.com/en/docs/claude-code)
- Internet access (for research)

## License

MIT
