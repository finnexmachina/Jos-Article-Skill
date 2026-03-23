# AI Detection Check & Humanization

Final gate before an article is considered done. Every draft must pass this.

---

## Step 1 — Run Detection Tools

Test the draft against AI detection tools. Use **at least 2** for a reliable read.

### Primary Tools (free, web-based)

Use WebFetch or the browser to submit the draft text to these:

| Tool | URL | Notes |
|------|-----|-------|
| **GPTZero** | https://gptzero.me | Widely used, scores by paragraph. Most reliable for long-form. |
| **ZeroGPT** | https://www.zerogpt.com | Fast, gives percentage score. |
| **Copyleaks** | https://copyleaks.com/ai-content-detector | Enterprise-grade, detailed breakdown. |
| **Sapling** | https://sapling.ai/ai-content-detector | Lightweight, quick check. |
| **Scribbr** | https://www.scribbr.com/ai-detector | Academic-focused, paragraph-level scoring. |

### How to test

1. Copy the full article text (no markdown formatting — plain text only)
2. Submit to at least 2 detectors
3. Record the score from each tool
4. If ANY tool flags >20% AI probability, the article needs a humanization pass

### Interpreting results

| Score | Verdict | Action |
|-------|---------|--------|
| 0–10% AI | Pass | Minor polish only, move to final review |
| 10–20% AI | Borderline | Review flagged paragraphs, light humanization |
| 20–50% AI | Fail | Full humanization pass on flagged sections |
| 50%+ AI | Hard fail | Significant rewrite needed — see humanization below |

---

## Step 2 — Identify AI Tells

Before rewriting, diagnose WHY it reads as AI. Common AI writing patterns:

### Structure tells
- Overly uniform paragraph length (all roughly the same)
- Predictable pattern: topic sentence → explanation → example → conclusion, every section
- Too-smooth transitions ("Furthermore," "Moreover," "Additionally," "In conclusion")
- Lists of exactly 3 or 5 items every time
- Every section the same length

### Language tells
- **Hedge stacking:** "It's important to note that..." "It's worth mentioning..."
- **Empty amplifiers:** "very," "really," "incredibly," "significantly"
- **Corporate filler:** "leverage," "utilize," "facilitate," "innovative," "cutting-edge"
- **AI favorites:** "delve," "tapestry," "landscape," "navigate," "multifaceted," "holistic," "robust," "seamless," "comprehensive"
- **Summarizer phrases:** "In summary," "To sum up," "All in all"
- **Overly balanced:** every pro has a con, every claim has a caveat — too neat
- **No contractions:** "do not" instead of "don't," "it is" instead of "it's"

### Voice tells
- No strong opinions — everything is measured and diplomatic
- No personality — could have been written by anyone
- No imperfection — too polished, no rough edges
- No specific personal experience or anecdote
- Uniform tone throughout — no emotional variation
- No humor, wit, or surprise

---

## Step 3 — Humanization Pass

For each flagged section, apply these techniques:

### Structural humanization
- **Vary paragraph length aggressively.** A one-sentence paragraph. Then a longer one with three or four ideas packed together. Then two sentences. Break the pattern.
- **Interrupt the flow.** Add an aside. A parenthetical. A fragment. Humans don't write in perfect logical chains.
- **Kill the transitions.** Remove "Furthermore" / "Moreover" / "Additionally." Just start the next idea. Readers can follow.
- **Rearrange.** Don't always lead with the topic sentence. Sometimes bury the point. Sometimes start with the example.
- **Vary section lengths.** One section can be 50 words, the next 300.

### Language humanization
- **Replace AI-favorite words.** "Delve" → "dig into" or "look at." "Landscape" → just name the thing. "Navigate" → "deal with" or "figure out." "Comprehensive" → "thorough" or just cut it.
- **Use contractions.** "Don't" not "do not." "It's" not "it is." Unless the stylesheet says otherwise.
- **Be specific instead of amplifying.** Not "very large company" but "12,000 employees across 30 countries."
- **Cut filler.** Remove "It's important to note that" — just state the thing.
- **Use the writer's actual vocabulary** from the stylesheet. Swap generic words for their signature phrases.

### Voice humanization
- **Add opinion.** Take a side. "This is the wrong approach" is more human than "there are arguments on both sides."
- **Add imperfection.** A self-correction. A concession. "I used to think X, but..."
- **Add specificity.** Replace generic examples with named, real ones. Not "many companies" — "Stripe did this in 2024."
- **Add texture.** A short sentence after a long one. A question. An incomplete thought followed by a dash —
- **Reference the stylesheet's signature moves.** The profiler identified what makes this writer distinctive. Lean into those.

### Rhythm humanization
- **Read it aloud.** If it sounds like a textbook, it reads as AI.
- **Mix sentence lengths.** Short. Then a longer one that takes its time building to the point. Then short again.
- **Use fragments intentionally.** Not every sentence needs a subject and verb. Sometimes just: "Exactly."
- **Front-load or back-load.** Don't always put the key word in the middle. "What nobody talks about is..." or ending with the punch.

---

## Step 4 — Re-test

After the humanization pass:

1. Run the revised text through the same 2+ detectors
2. Compare scores to the first round
3. If still >20% AI on any tool:
   - Identify which paragraphs are still flagged
   - Apply targeted humanization to just those paragraphs
   - Re-test those paragraphs individually
4. Repeat until all tools show <20% AI

---

## Step 5 — Report

Present the results to the user:

```
## AI Detection Results

### Before humanization
- [Tool 1]: [X]% AI detected
- [Tool 2]: [X]% AI detected

### After humanization
- [Tool 1]: [X]% AI detected
- [Tool 2]: [X]% AI detected

### Changes made
- [List of specific humanization changes applied]
```

---

## Step 6 — Product Authenticity Check

Separate from AI detection tools. This checks whether the article reads like it was written by someone who actually USES the product, not someone who Googled it.

### Signs of genuine product expertise (verify these are present):
- **Specific feature names** — uses the actual product terminology, not generic descriptions
- **Edition/tier awareness** — knows what's available where, not just "the product can do X"
- **Workflow knowledge** — describes HOW to do things, not just THAT you can
- **Known pain points** — mentions real frustrations that only users encounter
- **Insider shortcuts** — tips, workarounds, or non-obvious approaches
- **Accurate limitations** — knows the governor limits, the edge cases, the "gotchas"
- **Current state** — references recent updates, not outdated information
- **Ecosystem awareness** — knows the integrations, the community, the third-party tools

### Signs of fake expertise (fix these if found):
- Describes features in marketing language rather than practical terms
- Says "you can do X" without explaining how
- Uses the product name as a monolith ("Salesforce does X") instead of naming specific tools ("Salesforce Flow Builder lets you...")
- Gets edition availability wrong or doesn't mention it
- Describes capabilities that don't exist or existed in a prior version
- Uses competitor comparisons that sound like a marketing comparison chart rather than real experience
- Missing any mention of limitations, learning curves, or trade-offs

### Fix process:
1. Flag each section that lacks product depth
2. Add specific feature names, steps, edition details, and limitations
3. Replace marketing-speak with practitioner language
4. Add at least one "insider insight" that demonstrates real usage experience
5. Verify all additions against the product profile and official docs

---

## Important Notes

- **The stylesheet is your best defense.** A strong stylesheet based on real writing samples naturally produces less detectable text. The more samples fed to the profiler, the more human the output.
- **Don't over-humanize.** The goal isn't to add random chaos — it's to match real human writing patterns. The stylesheet defines what "human" looks like for THIS writer.
- **Detection tools aren't perfect.** They produce false positives on human writing too. If the text sounds right and matches the stylesheet, a borderline score may be acceptable. Ask the user.
- **Product expertise is the strongest AI differentiator.** Generic AI writes about products from the outside. An expert writes from the inside — knowing the shortcuts, the pain points, the "if you do X, watch out for Y." Lean into this.
- **Re-run the stylesheet passes after humanization** to make sure the voice is still consistent.
