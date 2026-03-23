---
name: article-setup
description: One-time setup for the article writing system. Builds your profile, product knowledge, writing style, and source library. Run this ONCE before using /article.
allowed-tools:
  - WebSearch
  - WebFetch
  - Read
  - Grep
  - Bash
  - Write
  - Edit
---

# Article Setup — One-Time Onboarding

Run this once. It builds everything `/article` needs to write for you.

**Important: for ANY list input (samples, screenshots, sources, rules, angles), always accept one item then ask "Add another? (yes/no)". Repeat until no.**

---

## Step 0 — Scaffold

```bash
ls "${CLAUDE_SKILL_DIR}/../article/samples" "${CLAUDE_SKILL_DIR}/../article/stylesheets" "${CLAUDE_SKILL_DIR}/../article/products" "${CLAUDE_SKILL_DIR}/../article/screenshots" "${CLAUDE_SKILL_DIR}/../article/knowledge-base.md" "${CLAUDE_SKILL_DIR}/../article/research-profile.md" "${CLAUDE_SKILL_DIR}/../article/tone-database.md" "${CLAUDE_SKILL_DIR}/../article/product-angles.md" 2>/dev/null
```

If anything missing → run `${CLAUDE_SKILL_DIR}/../article/scaffold.md`.

---

## Step 1 — Smart Setup (Profile)

Follow `${CLAUDE_SKILL_DIR}/../article/guided-setup.md` exactly. It handles:

1. **Q1-Q6:** Name, company, product, reader, reader needs, style — with AI research and probing between each question
2. **Source discovery:** Finds and presents product docs, community, blog, competitor sites — user accepts/rejects each
3. **Competitor discovery:** Finds and presents competitors — user accepts/rejects each
4. **Follow-up loops:** Publication, standing rules, blacklisted sources, recurring angles — each with add-another pattern
5. **Save progressively** to knowledge-base.md, research-profile.md, product-angles.md

---

## Step 2 — Product Knowledge

> I'm building a deep profile of [Product]. This takes a few minutes.

Run `${CLAUDE_SKILL_DIR}/../article/product-learner.md` inline.

Save to `${CLAUDE_SKILL_DIR}/../article/products/[product].md`.

---

## Step 3 — Style Profile (Writing Samples)

> I need to learn your writing voice. I'll need at least 5 articles to build a reliable style profile. Paste a URL to one of your published articles, or paste the text directly.

→ Accept one sample (URL → WebFetch, text → use directly).
→ Save to `${CLAUDE_SKILL_DIR}/../article/samples/sample-[N].md`.
→ **"Got it — that's [N] so far. Add another? (yes/no)"** → loop.

Check count:
- **5+** → "Great, enough for a solid profile." → run profiler
- **3-4** → "I can work with [N], but 5+ gives better results. Add more?"
- **1-2** → "I really need at least 5. Can you add more?"

If samples provided → run `${CLAUDE_SKILL_DIR}/../article/tone-profiler.md` inline.
If "skip" → proceed without, improve later.

---

## Step 4 — Readiness Check

Read all data files and verify:

### Critical (block if missing)

| Check | File | If missing |
|-------|------|-----------|
| Author name + role | knowledge-base.md → Author | Ask |
| Company with description | knowledge-base.md → Company | Research, present, confirm |
| Product with description | knowledge-base.md → Product | Research, present, confirm |
| Reader defined | knowledge-base.md → Audience | Ask |
| Reader needs defined | knowledge-base.md → Audience | Ask |
| At least 1 product source | research-profile.md → Product Sources | Search, present for accept/reject |
| Product profile exists | products/ | Run product-learner |

### Important (fill if easy)

| Check | File | If missing |
|-------|------|-----------|
| Product stance | knowledge-base.md → Product Positioning | Ask |
| At least 1 strength + 1 weakness | knowledge-base.md → Product Positioning | Infer, present for confirmation |
| At least 1 competitor | knowledge-base.md → Product Positioning | Search, present for accept/reject |
| Publication defined | knowledge-base.md → Publication | Ask |

### Nice-to-have (note, don't block)

| Check | File | If missing |
|-------|------|-----------|
| Stylesheet | stylesheets/ | Note: add samples anytime |
| Angles defined | product-angles.md | Suggest 2-3, present for accept/reject |
| Standing rules | knowledge-base.md → Standing Instructions | Note |

### Present readiness

> **Setup complete:**
> - Author: [name], [role] at [company] ✓
> - Product: [product] — [N] modules, [N] sources ✓
> - Audience: [reader description] ✓
> - Positioning: [stance] ✓
> - Sources: [N] product, [N] competitor ✓
> - Style: ✓ stylesheet / ⚠ verbal only
> - Rules: [N] ✓
> - Angles: [N] ✓
>
> You're ready. Run `/article` to write your first article.
