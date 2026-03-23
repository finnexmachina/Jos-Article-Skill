---
name: article
description: Write an authoritative article about your product. Loads your pre-built profile, product knowledge, and writing style, then researches and writes. Run /article-setup first if this is your first time.
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

# Article Writer

Loads everything built during setup and focuses 100% on writing one great article.

**Important: for ANY list input (screenshots, sources, context), always accept one item then ask "Add another? (yes/no)". Repeat until no.**

---

## Step 0 — Load Everything

Read ALL knowledge files at once. This is the foundation for the entire article.

### Required files — read all of these:

1. **Author & positioning:** `${CLAUDE_SKILL_DIR}/knowledge-base.md`
   - Who you are, your company, your product, your stance
   - Your audience and what they need
   - Your standing rules

2. **Research sources:** `${CLAUDE_SKILL_DIR}/research-profile.md`
   - Product sources (official docs, community, blog)
   - Competitor sources
   - Blacklisted sources
   - Standing research rules

3. **Product profile:** Read the .md file(s) in `${CLAUDE_SKILL_DIR}/products/`
   - Full product map, features, editions, limits, competitors, pricing
   - Real user sentiment, case studies

4. **Narrative angles:** `${CLAUDE_SKILL_DIR}/product-angles.md`
   - Recurring angles and the author's position on each

5. **Style:** Check `${CLAUDE_SKILL_DIR}/stylesheets/` for a stylesheet
   - If exists: load the full stylesheet (building blocks, vocabulary, voice, do/don't)
   - If not: use verbal style description from knowledge-base.md

6. **Past screenshots:** Check `${CLAUDE_SKILL_DIR}/screenshots/` for any existing screenshots relevant to this article's topic

### If setup hasn't been done:

Check if knowledge-base.md is still the empty template (just section headers, no data).

If empty:
> You haven't set up your profile yet. Run `/article-setup` first — it takes about 10 minutes and only needs to happen once.

Stop. Don't proceed without setup.

### If product profile is stale:

Check the "Last updated" date. If >30 days:
> Your product profile is from [date]. Want me to refresh it before writing? (yes/no)

If yes → run `${CLAUDE_SKILL_DIR}/product-learner.md` inline.

### Confirm loaded:

After loading, hold all this knowledge in context. Don't summarize it back to the user — just confirm:
> Loaded: profile, product ([N] modules), [N] sources, [stylesheet name / verbal style]. Ready.

---

## Step 1 — Gather Intent

Take whatever the user already provided. Only ask for what's missing:

1. **Angle** — what's the specific angle or thesis? If angles exist in product-angles.md, suggest relevant ones: "You've written about [angle] before — is this similar, or a new angle?"
2. **Audience** — default from knowledge-base.md. Only ask if this article targets someone different.
3. **Purpose** — inform, persuade, educate, compare, thought leadership?
4. **Format** — blog post, long-form, opinion piece, how-to, case study, comparison?
5. **Length** — target word count?
6. **Context** — specific data, links, or details to include?

### Screenshots

If the user attached screenshots, read them immediately.

If the article covers specific product UI and no screenshots were attached:
> "This article covers [feature/module]. Screenshots make a huge difference — they let me reference real field names, button labels, settings, and limits instead of paraphrasing docs. An article that describes what the screen actually looks like reads as expert.
>
> Got a screenshot of [specific screen]? Paste or say 'skip'."

→ Accept one → read → extract UI details.
→ **"Add another screenshot? (yes/no)"** → loop.
→ Save to `${CLAUDE_SKILL_DIR}/screenshots/[module]/`

Extracted UI details are **verified** and outrank documentation claims.

### Confirm plan

Before researching, confirm:
> Here's what I'll write:
> - **Angle:** [angle]
> - **Audience:** [audience] (from your profile, unless different)
> - **Format:** [format], ~[length] words
> - **Product areas:** [features/modules from the product profile that are relevant]
> - **Using:** [N] product sources, [N] competitor sources, product profile ([N] modules), [stylesheet name]
>
> I'll run 10-30+ searches to add depth beyond your existing sources. After research, I'll present everything with source URLs for you to double-check. Ready?

---

## Step 2 — Research

Load `${CLAUDE_SKILL_DIR}/research-profile.md` and follow `${CLAUDE_SKILL_DIR}/research.md`.

**The product profile is already loaded — it's the foundation.** Research adds:
- What's new since the profile was last updated
- Angle-specific depth the profile doesn't cover
- Competitive context for this specific angle
- Fresh data, quotes, case studies, user perspectives

**Cross-reference with what's already known.** If research contradicts the product profile, flag it:
> "My research found [X] but your product profile says [Y]. Which is current?"

Present the full research summary with source URLs. Ask:
> **Double-check the sources** — you know your domain better than I do. Flag anything wrong, outdated, or from a source you don't trust. Anything I should dig deeper on?

Wait for confirmation before writing.

---

## Step 3 — Write

Follow `${CLAUDE_SKILL_DIR}/writing.md`:

1. **Outline** — propose headline, subtitle, sections, product depth map, word count. Wait for approval.

2. **Draft** — write section by section using:
   - Product profile for accurate feature claims, editions, limits
   - Research findings for angle-specific depth and freshness
   - Knowledge base for author's positioning and expertise framing
   - Screenshots for verified UI details
   - Audience profile for appropriate depth and tone

3. **Apply stylesheet** (if exists):
   - Building blocks pass — paragraph lengths, formatting elements, section structure
   - Language pass — signature vocabulary, sentence construction
   - Voice pass — formality, warmth, confidence, rhetorical devices
   - Tone calibration — adjust for this article's type and audience
   - Do/Don't check
   - Sound check — does it match the sample phrases?

4. **Product accuracy check** — verify every claim:
   - Feature names correct?
   - Edition/tier stated where relevant?
   - Pricing current?
   - Competitive comparisons fair and verified from competitor's own docs?
   - No unsourced claims?
   - Flag anything unverified: "[Unverified] — please confirm before publishing"

5. **Present draft** with:
   - Headline and subtitle
   - Full article
   - Word count
   - Stylesheet applied (name) or verbal style used
   - Key sources that informed the content
   - Any unverified claims flagged

6. **Iterate** until the user is satisfied. On each revision, re-run stylesheet + accuracy passes.

7. **AI detection check** (mandatory) — follow `${CLAUDE_SKILL_DIR}/ai-detection.md`:
   - Run through 2+ detection tools
   - If >20% AI → humanization pass
   - Product authenticity check
   - Re-test until passing
   - Report before/after scores

---

## After the Article

- If the user corrected a product fact → update the product profile
- If screenshots were provided → already saved to `screenshots/`
- If a new angle emerged → ask: "This article explored [angle]. Add it to your recurring angles? (yes/no)"
- If style feedback was given → note for stylesheet refinement
- If no stylesheet exists → ask: "Want to use this article as a writing sample for your style profile?"
