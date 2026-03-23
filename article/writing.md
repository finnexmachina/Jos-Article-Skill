# Writing Process

Turn product research into an authoritative article that demonstrates genuine expertise.

---

## Step 0 — Load the Stylesheet

Read the user's stylesheet from `${CLAUDE_SKILL_DIR}/stylesheets/[name].md`.
- Keep it loaded throughout the entire writing process
- Every decision below is filtered through the stylesheet
- If no stylesheet exists, use the user's verbal style description from setup. The writing will improve once they provide samples.

---

## Step 1 — Outline

Before writing, propose an outline:

- **Headline** — compelling, specific, makes a promise to the reader
- **Subtitle** — expands on the headline, sets expectations
- **Section breakdown** — each section with a one-line summary
- **Key points per section** — the argument or information each delivers
- **Product depth map** — which sections go deep on features, which stay high-level
- **Estimated word count** — per section and total

The outline should show WHERE product expertise appears — it shouldn't be evenly distributed. Some sections go deep into feature mechanics; others pull back to strategy or market context.

Present the outline. Wait for approval before drafting.

## Step 2 — Write the First Draft

Write section by section, incorporating:
- **Product profile** as the factual backbone
- **Angle-specific research** for depth beyond the profile
- **Real user perspectives** for authenticity
- **Competitive context** where relevant
- **Knowledge base** for the author's positioning and expertise framing

### Product depth rules

When explaining product features or capabilities:
- **Name the specific feature/tool** — not "Salesforce has automation" but "Salesforce Flow Builder lets you create automated workflows with a visual drag-and-drop interface"
- **Specify the edition/tier** — "Available in Enterprise Edition and above" or "Included in all paid plans"
- **Describe the actual workflow** — step-by-step what a user does, not abstract descriptions
- **State the limits** — governor limits, record caps, API call limits, whatever constrains it
- **Acknowledge the learning curve** — if it's complex to set up, say so. This builds trust.
- **Compare to alternatives** — how does the competitor handle this? What's the tradeoff?
- **Use real numbers** — "$25/user/month" not "competitively priced". "150 API calls per day" not "generous API limits."

## Step 3 — Apply the Stylesheet

Revise the draft against the stylesheet systematically. The stylesheet includes a **Building Blocks Blueprint** with exact measurements — paragraph lengths, formatting element frequencies, section structure. Match these precisely.

1. **Building blocks pass** — check the draft against the Building Blocks Blueprint:
   - Paragraph count in target range?
   - Paragraph lengths match the measured averages? (sentences per paragraph, word count)
   - One-sentence paragraphs used at the right frequency and placement?
   - Length rhythm matches the pattern? (e.g., medium-short-long-short)
   - Formatting elements match? (right number of lists, bold usage, quotes, em-dashes, etc.)
   - Elements they never use are absent?
   - Section count and section lengths in range?
   - Opening and closing match their patterns?
2. **Language pass** — swap in signature vocabulary, remove anti-pattern words, match sentence length and construction
3. **Voice pass** — check formality/warmth/confidence levels, apply rhetorical devices, inject signature moves
4. **Tone calibration** — adjust for the specific article type and audience
5. **Do/Don't check** — final pass against the stylesheet's always/never rules
6. **Sound check** — read it against sample phrases. Does it sound like it came from the same writer?

## Step 4 — Product Accuracy Check

**Mandatory.** Before presenting to the user, verify:

- [ ] Every product feature claim is accurate per official documentation
- [ ] Edition/tier availability is stated where relevant
- [ ] Pricing information is current (note the date if uncertain)
- [ ] Competitive comparisons are fair and verified from competitor's own materials
- [ ] No features are attributed to the wrong product or edition
- [ ] Technical details (API limits, field types, permissions) are correct
- [ ] Screenshots or UI descriptions match the current interface (flag if unsure)
- [ ] The article reflects the author's stated product positioning (from knowledge base)
- [ ] No claims are unsourced — everything traces back to research

If anything can't be verified, flag it explicitly:
> **[Unverified]:** I couldn't confirm [claim]. Please verify before publishing.

## Step 5 — Article Quality Rules

These apply regardless of stylesheet:

- **Strong opening** — the first paragraph earns the second. Hook the reader.
- **Expert, not generic** — every section should contain something only a product expert would know.
- **Feature depth where it matters** — don't skim the product mechanics. Go deep on the parts that serve the angle.
- **Evidence-backed** — claims supported by research. Cite sources.
- **Honest about weaknesses** — acknowledging limitations builds more trust than cheerleading.
- **Active voice** — default to active. Passive only when the actor is irrelevant.
- **Cut filler** — every sentence earns its place.
- **Specific over vague** — names, numbers, editions, tiers. Not "many users" but "G2 reviewers rate it 4.3/5 across 12,000 reviews."
- **Strong closing** — end with insight, not summary.
- **Proofread** — no typos, no broken formatting, no placeholder text.

## Step 6 — Present

Show the user:

- The **headline and subtitle**
- The **full article**
- **Word count**
- **Stylesheet applied:** [name]
- **Product profile used:** [product] (last updated: [date])
- **Research sources:** key sources that informed the content
- **Unverified claims:** anything that needs the user's confirmation

Then ask:
> Want me to adjust the voice, depth, angle, or structure? Any product details I got wrong?

Iterate until satisfied. On each revision, re-run stylesheet passes and product accuracy check.

## Step 7 — AI Detection Check

**Mandatory. No article is finished until it passes.**

Follow `${CLAUDE_SKILL_DIR}/ai-detection.md`:

1. Run through 2+ AI detection tools
2. If flagged >20% AI → humanization pass
3. Product authenticity check (see below)
4. Re-test until passing
5. Report before/after scores
