---
name: article
description: Research and craft authoritative articles about your company's product. Handles setup, product research, style profiling, and writing in one unified flow. Use when the user wants to write an article.
argument-hint: [topic or angle]
allowed-tools:
  - WebSearch
  - WebFetch
  - Read
  - Grep
  - Bash
  - Write
  - Edit
---

# Article Writer — Product Authority System

One command does everything. The user never runs a separate command.

**Important: for ANY list input (samples, screenshots, sources, rules, angles), always accept one item then ask "Add another? (yes/no)". Repeat until no.**

---

## Step 0 — Check State

```bash
ls "${CLAUDE_SKILL_DIR}/samples" "${CLAUDE_SKILL_DIR}/stylesheets" "${CLAUDE_SKILL_DIR}/products" "${CLAUDE_SKILL_DIR}/screenshots" "${CLAUDE_SKILL_DIR}/knowledge-base.md" "${CLAUDE_SKILL_DIR}/research-profile.md" "${CLAUDE_SKILL_DIR}/tone-database.md" "${CLAUDE_SKILL_DIR}/product-angles.md" 2>/dev/null
```

If anything missing → run `${CLAUDE_SKILL_DIR}/scaffold.md`.

Then check what exists:
- Read `${CLAUDE_SKILL_DIR}/knowledge-base.md` — filled in or just template?
- Check `${CLAUDE_SKILL_DIR}/products/` for .md files
- Check `${CLAUDE_SKILL_DIR}/stylesheets/` for .md files

Route:

| Profile | Product | Stylesheet | Go to |
|---------|---------|-----------|-------|
| Empty | — | — | Step 1 (full onboarding) |
| Done | Empty | — | Step 2 (product knowledge) |
| Done | Done | Empty | Step 3 (style profile) |
| Done | Done | Done | Step 4 (readiness check) on first article, then Step 5 (gather intent) on subsequent |

---

## Step 1 — Smart Setup (Profile)

Follow `${CLAUDE_SKILL_DIR}/guided-setup.md` exactly. It handles:

1. **Q1-Q6:** Name, company, product, reader, reader needs, style — with AI research and probing between each question
2. **Source discovery:** Finds and presents product docs, community, blog, competitor sites — user accepts/rejects each
3. **Competitor discovery:** Finds and presents competitors — user accepts/rejects each
4. **Follow-up loops:** Publication, standing rules, blacklisted sources, recurring angles — each with add-another pattern
5. **Save:** Writes all confirmed data to knowledge-base.md, research-profile.md, product-angles.md progressively as answers come in

After setup completes, tell the user:
> Profile complete. Now I'll build a deep knowledge base of [Product]. This takes a few minutes.

→ Continue to Step 2.

---

## Step 2 — Product Knowledge

Check `${CLAUDE_SKILL_DIR}/products/` for a profile.

**If no profile exists:**
> Building a deep profile of [Product]...

Run `${CLAUDE_SKILL_DIR}/product-learner.md` inline. Don't ask — just do it.

**If profile exists but >30 days old:**
> Your [Product] profile is from [date]. Want me to refresh it?

If yes → re-run product-learner. If no → load as-is.

**If profile exists and fresh:** Load silently.

After product profile is ready, tell the user:
> Product profile ready — [N] modules covered, [N] sources.

→ Continue to Step 3.

---

## Step 3 — Style Profile (Writing Samples)

Check `${CLAUDE_SKILL_DIR}/stylesheets/` for a stylesheet.

**If no stylesheet exists:**
> Last setup step — I need to learn your writing voice. I'll need at least 5 articles to build a reliable style profile. Paste a URL to one of your published articles, or paste the text directly.

→ Accept one sample (URL → WebFetch, text → use directly).
→ Save to `${CLAUDE_SKILL_DIR}/samples/sample-[N].md`.
→ **"Got it — that's [N] so far. Add another? (yes/no)"** → loop until no.

After the loop, check the count:
- **5+ samples** → "Great, that's enough for a solid profile." → run profiler
- **3-4 samples** → "I can work with [N], but 5+ gives much better results. Want to add more?" → if no, proceed
- **1-2 samples** → "That's not enough for a reliable profile — I really need at least 5. Can you add more?" → push for more, but don't hard-block

If samples provided → run `${CLAUDE_SKILL_DIR}/tone-profiler.md` inline. Tell user:
> Analyzing your writing style...

Then present the stylesheet summary for confirmation.

If "skip" → proceed without. Note: style improves with feedback over time.

**If stylesheet exists:** Load silently.

→ Continue to Step 4.

---

## Step 4 — Onboarding Complete / Readiness Check

**This runs before the FIRST article only.** On subsequent runs, skip to Step 5.

Read all data files and verify completeness:

### Critical (must have — block if missing)

| Check | File | If missing |
|-------|------|-----------|
| Author name + role | knowledge-base.md → Author | Ask |
| Company with description | knowledge-base.md → Company | Research, present, confirm |
| Product with description | knowledge-base.md → Product | Research, present, confirm |
| Reader defined | knowledge-base.md → Audience | Ask |
| Reader needs defined | knowledge-base.md → Audience | Ask |
| At least 1 product source | research-profile.md → Product Sources | Search, present for accept/reject |
| Product profile exists | products/ | Run product-learner (should already be done in Step 2) |

### Important (should have — fill if easy, note if not)

| Check | File | If missing |
|-------|------|-----------|
| Product stance (advocate/balanced/critical) | knowledge-base.md → Product Positioning | Ask: "How do you position [Product] — advocate, balanced, or critical?" |
| At least 1 strength + 1 weakness | knowledge-base.md → Product Positioning | Infer from product research, present for confirmation |
| At least 1 competitor with positioning | knowledge-base.md → Product Positioning | Search, present for accept/reject |
| At least 1 competitor source | research-profile.md → Competitor Sources | Search, present for accept/reject |
| Publication defined | knowledge-base.md → Publication | Ask |

### Nice-to-have (note but don't block)

| Check | File | If missing |
|-------|------|-----------|
| Stylesheet exists | stylesheets/ | Note: "No writing style profile yet. Add samples anytime to improve." |
| At least 1 angle defined | product-angles.md | Suggest 2-3 based on product + audience, present each for accept/reject |
| Standing rules beyond defaults | knowledge-base.md → Standing Instructions | Note |
| Blacklisted sources | research-profile.md → Blacklisted | Note |

### Fill gaps

For each missing item:
1. **If AI can research it** → search, present findings, ask to accept/reject
2. **If only the user can answer** → ask directly
3. **If nice-to-have** → note it, don't block

### Present readiness

> **Onboarding complete:**
> - Author: [name], [role] at [company] ✓
> - Product: [product] ✓
> - Product profile: [N] modules, [N] sources ✓
> - Audience: [reader description] ✓
> - Positioning: [stance] ✓
> - Sources: [N] product, [N] competitor ✓
> - Style: ✓ stylesheet / ⚠ verbal only
> - Rules: [N] ✓
> - Angles: [N] ✓ / ⚠ none yet
>
> Ready to write. What's the article about?

---

## Step 5 — Gather Intent

**This is the entry point for every article after onboarding.**

Take whatever the user already provided. Only ask for what's missing:

1. **Angle** — suggest from product-angles.md if angles exist
2. **Audience** — default from knowledge-base.md. Only ask if different.
3. **Purpose** — inform, persuade, educate, compare, thought leadership?
4. **Format** — blog post, long-form, opinion piece, how-to, case study, comparison?
5. **Length** — target word count?
6. **Context** — specific data, links, or details to include?

### Screenshots

If the user attached screenshots, read them immediately.

If the article covers specific product UI and no screenshots were attached, explain why they matter and ask:
> "This article covers [feature/module]. Screenshots make a huge difference here — they let me reference real UI details like actual field names, button labels, settings options, and limits instead of paraphrasing documentation. An article that describes what the screen actually looks like reads as expert. One that paraphrases docs reads as research.
>
> Got a screenshot of [specific screen]? Paste or say 'skip'."

→ Accept one → read → extract UI details (field names, labels, settings, limits, layout).
→ **"Add another screenshot? (yes/no)"** → loop.
→ Save to `${CLAUDE_SKILL_DIR}/screenshots/[module]/`

Extracted UI details are **verified** and outrank documentation claims. When writing, explicitly reference what the screenshot showed: "In the Flow Builder screen, you'll see a 'New Flow' button in the top right..." — this level of specificity is only possible with screenshots.

### Sources

After gathering intent, confirm the research approach:
> "For this article I'll use your [N] trusted sources plus the product profile ([N] modules, [N] sources). I'll also extend beyond those — searching for recent coverage, user perspectives, competitive context, and data specific to this angle. I run 10-30+ searches and fetch the full pages, not just snippets.
>
> After research, I'll present everything I found with source URLs. **Double-check the sources** — I surface what I find, but you know your domain better. Flag anything that looks wrong, outdated, or from a source you don't trust.
>
> Ready to research?"

---

## Step 6 — Research

Load `${CLAUDE_SKILL_DIR}/research-profile.md` and follow `${CLAUDE_SKILL_DIR}/research.md`.

Product profile is the foundation. Research adds angle-specific depth:
- What's new since the profile was last updated?
- What's specific to THIS article's angle?
- What competitive or market context does this angle need?

Go deep. Maximize tool calls. Present findings and wait for user confirmation before writing.

---

## Step 7 — Write

Follow `${CLAUDE_SKILL_DIR}/writing.md`:

1. Propose outline → wait for approval
2. Draft with product profile as factual backbone
3. Apply stylesheet (if exists) — building blocks pass first, then 5 more passes
4. Product accuracy check — verify every claim
5. Present draft with sources and any unverified flags
6. Iterate until user is satisfied
7. AI detection check (mandatory) — `${CLAUDE_SKILL_DIR}/ai-detection.md`

---

## After Every Article

Silently improve the system:

- If the user corrected a product fact → update the product profile
- If screenshots were provided → already saved to `screenshots/`
- If a new narrative angle emerged → ask: "This article explored [angle]. Add it to your recurring angles? (yes/no)"
- If the user gave style feedback → note for stylesheet refinement
- If this was the first article without a stylesheet → ask: "Want to use this article as a writing sample for your style profile?"
