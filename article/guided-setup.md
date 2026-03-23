# Smart Setup

Everything happens in the console. The user never opens a file.

---

## Core Principles

**1. Every answer triggers AI action.** Don't just collect answers — research, infer, and verify between questions. Each answer makes the next question smarter.

**2. Present what you find, ask to accept.** When research turns up sources, competitors, or facts — show them to the user and ask: "Accept this? (yes/no)". Never silently add things.

**3. Ask follow-ups when something interesting comes up.** The 6 core questions are a spine, not a script. If an answer reveals something worth probing ("we focus on financial services") — follow that thread before moving on.

**4. Add-another loop for all lists.** Accept one item → "Add another? (yes/no)" → repeat. Applies to: samples, sources, rules, angles, screenshots, competitors.

---

## The Flow

### Q1 — "What's your name and role?"

Accept answer.

**AI reasons from role:**
- What type of content does this role typically produce?
- What's their likely relationship to the product? (advocate, analyst, technical, strategic)
- What depth and tone would their audience expect?

Don't share this reasoning yet. It shapes how you ask the remaining questions.

---

### Q2 — "What company do you work for?"

Accept answer.

**AI acts immediately:**
- WebSearch "[Company]"
- WebFetch company homepage

**Present findings:**
> I found that [Company] is [one-line description]. You offer [key products/services]. Is that right?

Accept corrections.

**If the company has multiple products, probe:**
> I see [Company] has [Product A], [Product B], [Product C]. Which one do you write about?

This naturally leads into Q3.

---

### Q3 — "What product do you write about?"

Accept answer. (May already be answered from Q2 probing.)

**AI acts immediately:**
- WebSearch "[Product] documentation"
- WebSearch "[Product] community forum"
- WebSearch "[Product] blog"
- WebSearch "[Product] pricing"
- WebSearch "[Product] features overview"
- WebFetch the product's main page

**Present discovered sources for acceptance:**
> I found these for [Product]:
> - Docs: [URL] — accept as trusted source? (yes/no)
> - Community: [URL] — accept? (yes/no)
> - Blog: [URL] — accept? (yes/no)
> - Pricing page: [URL] — accept? (yes/no)

For each yes → add to research-profile.md as Tier 1 source.
For each no → discard.

**Then ask:**
> "Any other sources you rely on for [Product]?"

→ Accept one. "Add another? (yes/no)" → loop.

**AI also searches for competitors:**
- WebSearch "[Product] vs" / "[Product] alternatives [current year]"

**Present competitors for acceptance:**
> Based on my research, the main competitors seem to be [A], [B], [C]. Sound right?

Accept corrections. User might add or remove.

→ "Any others? (yes/no)" → loop.

For each accepted competitor, immediately:
- WebSearch "[Competitor] website"
- WebSearch "[Competitor] documentation"
- Present: "I found [Competitor]'s docs at [URL]. Accept as competitor source? (yes/no)"

---

### Q4 — "Who are your articles for? Describe your ideal reader."

Accept answer.

**AI reasons and probes:**

Based on the reader description + the product, ask a smart follow-up. Examples:

- If reader is evaluating: "Are they comparing against specific competitors, or exploring the category for the first time?"
- If reader is technical: "Are they hands-on admins/developers, or technical decision-makers?"
- If reader is executive: "Are they the budget holder, or the one recommending to the budget holder?"
- If the product serves specific industries: "Are your readers in a specific industry, or general?"

Each follow-up answer gets stored and may trigger more research:
- Industry mentioned → WebSearch "[Product] + [industry]" → may discover industry-specific features or certifications
- Present findings: "I found that [Product] has a [Industry] edition. Do you cover that? (yes/no)"

---

### Q5 — "What does that reader need from your articles? What problem are you solving for them?"

Accept answer.

**AI reasons about content strategy:**

Based on reader + their needs + product + role, infer:
- What article formats will work best (how-tos? comparisons? thought leadership?)
- What depth is needed (overview vs. deep technical?)
- What the reader already knows (don't over-explain basics)

**Share one useful inference:**
> Given that your readers are [audience] looking for [need], it sounds like [format type] articles would work well — articles that [do X]. Is that right, or do you approach it differently?

This helps calibrate without over-asking.

---

### Q6 — "How would you describe your writing style in a few words?"

Accept answer.

**AI probes for specificity:**

Based on their style description, ask ONE clarifying question:

- "Authoritative" → "Do you back claims with data and stats, or more with real-world experience?"
- "Friendly" → "Friendly as in casual/conversational, or friendly as in warm but still professional?"
- "Technical" → "Technical meaning you include code/configs, or technical meaning you go deep on architecture?"
- "Data-driven" → "Do you cite specific studies and numbers, or more trend-level observations?"

This shapes the stylesheet more precisely.

---

## Follow-Up Loops

After the 6 core questions + probing, run these. Each uses the add-another pattern.

### Publication
> "Where do your articles get published?"

→ Accept. "Anywhere else? (yes/no)" → loop.

### Standing Rules
> "Any rules for every article? e.g., 'always link to official docs' or 'use American English' or 'never trash competitors'"

→ Accept one. "Add another rule? (yes/no)" → loop.

### Blacklisted Sources
> "Any sources to specifically avoid?"

→ Accept one. "Add another? (yes/no)" → loop. Or "none" to skip.

### Recurring Angles
> "What angles or themes keep coming up in your writing? e.g., 'total cost of ownership' or 'admin complexity'"

→ Accept one. For each, ask a brief follow-up: "What's your take on that?" (one sentence is fine).
→ "Add another angle? (yes/no)" → loop.

Write each to `${CLAUDE_SKILL_DIR}/product-angles.md`.

---

## Writing Samples

> "Last step — I need to learn your writing voice. I'll need at least 5 articles to build a reliable style profile. Paste a URL to one of your published articles, or paste the text directly."

→ Accept one (URL → WebFetch, text → use directly).
→ Save to `${CLAUDE_SKILL_DIR}/samples/sample-[N].md`.
→ **"Got it — that's [N] so far. Add another? (yes/no)"** → loop.

After the loop, check the count:
- **5+ samples** → "Great, that's enough for a solid profile." → run profiler
- **3-4 samples** → "I can work with [N], but 5+ gives much better results. Want to add more?"
- **1-2 samples** → "That's not enough for a reliable profile — I really need at least 5. Can you add more?"

If "skip" → proceed without stylesheet, refine over time from feedback.

After enough samples → run `${CLAUDE_SKILL_DIR}/tone-profiler.md`.

---

## When to Save

**Save progressively, not at the end.** After each question + AI research:
- Q1 answers → write to knowledge-base.md → Author section immediately
- Q2 answers + research → write to knowledge-base.md → Company section immediately
- Q3 answers + research → write to knowledge-base.md → Product section + research-profile.md → Product Sources immediately
- Q3 competitors → write to knowledge-base.md → Positioning → Competitors + research-profile.md → Competitor Sources immediately
- Q4 answers → write to knowledge-base.md → Audience immediately
- Q5 answers + inference → write to knowledge-base.md → Audience section immediately
- Q6 answers → store for stylesheet (not written to file until profiler runs)
- Follow-up loops → write each to the appropriate file as soon as confirmed

This way if the user disconnects or the session is interrupted, whatever was completed is saved.

---

## Completion

> Setup done.
> - **Author:** [name], [role] at [company]
> - **Product:** [product]
> - **Audience:** [reader description]
> - **Sources:** [N] trusted, [N] competitor, [N] blacklisted
> - **Angles:** [N] defined
> - **Samples:** [N] collected
> - **Rules:** [N] standing rules
>
> Run `/article` to write your first article. All your knowledge is loaded fresh each time — nothing from this setup conversation carries over, so `/article` gets full focus on your article.
>
> One folder = one identity. Different company or voice? New folder, fresh copy from the repo.
