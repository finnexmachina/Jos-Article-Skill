# Tone & Style Profiler

Deep analysis pipeline that takes sample articles and builds a comprehensive stylesheet the writing process can follow to replicate the user's voice exactly.

---

## Input

Read all `.md` files in `${CLAUDE_SKILL_DIR}/samples/`.

Samples are collected during setup via the console — the user pastes URLs or text, one at a time, using the "add another? (yes/no)" loop. They're saved as `sample-1.md`, `sample-2.md`, etc.

Additional samples can come from:
- URLs the user provides (WebFetch them)
- Text pasted in the conversation
- File paths the user specifies (Read them)

**Minimum: 5 samples.** Fewer than 5 and the profiler can't reliably separate your core style from one-off choices. 5-10 is strong. 10+ is best.

---

## Pipeline

### Stage 1 — Collect & Catalog

Gather all samples. For each, record:
- Source (file, URL, pasted)
- Word count
- Type (blog post, article, newsletter, report, opinion piece, social post, etc.)
- Apparent audience (who was this written for?)
- Apparent purpose (inform, persuade, connect, sell, etc.)

Present the catalog: "I've collected N samples. Here's what I see: [list]. Ready to analyze?"

---

### Stage 2 — First Pass: Surface-Level Read

Read every sample end to end. For each, capture first impressions:
- What's the overall feel?
- What stands out immediately?
- What would a reader remember after closing it?
- How does it compare to generic writing on the same topic?

This pass is about gut-level pattern recognition before structured analysis.

---

### Stage 3 — Second Pass: Building Blocks Inventory

**Quantitative analysis.** Count everything. Measure everything. This is what makes the stylesheet precise instead of vague.

For EACH sample, build a complete inventory:

**Article-Level Metrics**
- Total word count
- Total paragraph count
- Total section/header count
- Reading time estimate
- Ratio of text to formatting elements (lists, quotes, etc.)

**Paragraph Measurements**
- Word count per paragraph (list every one, then calculate: min, max, average, median)
- Sentences per paragraph (list every one, then: min, max, average, median)
- One-sentence paragraph count and where they appear (opening, mid-section, closing, after lists)
- Longest paragraph (word count + where it appears)
- Shortest paragraph (word count + where it appears)
- Length variation pattern: is it uniform? Alternating long-short? Front-loaded? Back-loaded?
- Paragraph-to-paragraph length sequence (e.g., "long, short, medium, short, long" — map the rhythm)

**Formatting Elements — Full Count**

| Element | Count | Where used | How used |
|---------|-------|-----------|----------|
| **Headers (H2)** | [N] | [positions] | [as questions? statements? single words?] |
| **Subheaders (H3+)** | [N] | [positions] | [style] |
| **Bulleted lists** | [N] | [positions] | [items per list: min/max/avg] |
| **Numbered lists** | [N] | [positions] | [items per list: min/max/avg] |
| **Block quotes** | [N] | [positions] | [own words or citing others?] |
| **Bold text** | [N instances] | [what gets bolded?] | [key terms? emphasis? leads?] |
| **Italic text** | [N instances] | [what gets italicized?] | [titles? emphasis? foreign words?] |
| **Inline code / monospace** | [N] | [what for?] | [product names? commands? terms?] |
| **Links** | [N] | [to what?] | [inline or footnote style?] |
| **Images/figures** | [N] | [positions] | [screenshots? diagrams? stock?] |
| **Tables** | [N] | [what data?] | [comparison? reference? data?] |
| **Pull quotes / callouts** | [N] | [positions] | [own emphasis or reader highlights?] |
| **Horizontal rules / dividers** | [N] | [between what?] | [section breaks? topic shifts?] |
| **Footnotes / endnotes** | [N] | [what type of info?] | |
| **Parenthetical asides** | [N] | | [short or long? serious or witty?] |
| **Em-dashes (—)** | [N] | | [for asides? lists? dramatic pauses?] |
| **Ellipsis (...)** | [N] | | [trailing off? omission? suspense?] |

**Section Architecture**
- How many sections (H2-level) per article?
- Average section length (words, paragraphs)
- Section length variation (are some sections much longer than others?)
- Do sections follow a pattern? (intro section → deep section → deep section → conclusion)
- What's in the first section? (context? hook? thesis?)
- What's in the last section? (summary? CTA? forward look? question?)

**Opening Patterns**
- How do they start? (question, bold claim, story, data point, direct address, context-setting, scene-setting)
- How many sentences before reaching the main point?
- Is there a hook? What type?
- Does the opening paragraph follow a different structure than body paragraphs?

**Closing Patterns**
- How do they end? (CTA, summary, question, callback to opening, forward-looking statement, provocative thought)
- Is there a signature move in the close?
- How long is the closing section vs. average section?

**Transitions Between Sections**
- How do sections connect? (transitional phrases, white space only, subheaders as transitions)
- Are there bridge sentences between sections?
- Do new sections reference the previous one or start fresh?

**Flow & Pacing**
- Where do they speed up (short paragraphs, fragments, lists)?
- Where do they slow down (longer paragraphs, detailed explanation, examples)?
- Rhythm pattern: map the paragraph lengths across the whole piece as a sequence
- Where do formatting elements cluster? (lists in the middle? bold at section starts?)

**Visual Density**
- How much white space? (frequent paragraph breaks = airy; long paragraphs = dense)
- Text-to-list ratio (how much is prose vs. formatted lists?)
- Do they break up long text with formatting elements, or let it flow?

---

### Stage 3B — Building Blocks Summary

After inventorying all samples, create a summary table:

```
## Building Blocks Profile

### Article Shape
- Typical length: [X–Y words]
- Sections: [N–N], averaging [X words] each
- Paragraphs: [N–N] per article

### Paragraph Blueprint
- Length: [X–Y sentences] (avg [Z])
- Word count: [X–Y words] (avg [Z])
- One-sentence paragraphs: [frequency and placement]
- Rhythm: [description of length pattern]

### Formatting Fingerprint
| Element | Frequency | Usage Pattern |
|---------|-----------|---------------|
| Headers | [per article avg] | [style] |
| Bulleted lists | [per article avg] | [items per list, placement] |
| Numbered lists | [per article avg] | [usage] |
| Bold | [per article avg] | [what gets bolded] |
| Block quotes | [per article avg] | [how used] |
| Tables | [per article avg] | [how used] |
| Links | [per article avg] | [inline style] |
| Em-dashes | [per article avg] | [how used] |

### What They Use Most
[Top 3 formatting elements and how they use them]

### What They Never Use
[Formatting elements absent from all samples]
```

This summary goes directly into the stylesheet as a concrete blueprint that the writing process follows.

---

### Stage 4 — Third Pass: Language Fingerprint

Analyze the exact word-level and sentence-level habits.

**Vocabulary**
- Vocabulary level (simple, mixed, technical, academic)
- Domain-specific terms they use (list them)
- Words they use often — their "signature vocabulary" (list 10–20)
- Words/phrases they notably AVOID
- Filler words or verbal tics (list any)
- Preference for Anglo-Saxon vs. Latinate words

**Sentence Construction**
- Average sentence length (count words across samples)
- Sentence length range (shortest to longest typical sentence)
- Ratio of simple/compound/complex sentences
- Use of fragments or incomplete sentences
- Use of parenthetical asides
- Use of dashes (em-dash, en-dash) vs. commas vs. parentheses
- Active vs. passive voice ratio
- Where do they put the key information — beginning or end of sentence?

**Punctuation & Mechanics**
- Exclamation point frequency
- Question mark usage (rhetorical vs. real)
- Ellipsis usage
- Colon/semicolon frequency
- Oxford comma (yes/no)
- Capitalization style (title case, sentence case, unconventional)
- Emoji usage (never, rare, frequent — which ones)
- Contraction frequency

**Rhetorical Devices**
- Analogies/metaphors (frequency and type — are they from a specific domain?)
- Repetition (anaphora, callbacks, refrains)
- Contrast/juxtaposition
- Humor style (self-deprecating, observational, dry, absurdist, none)
- Direct address to reader
- Rhetorical questions
- Use of stories or anecdotes
- Use of data/numbers to support points
- Use of quotes or references

---

### Stage 5 — Fourth Pass: Voice & Personality

Capture the intangible qualities.

**Authority & Stance**
- Formality scale: 1–10
- Confidence scale: 1–10 (do they hedge or assert?)
- Specificity scale: 1–10 (vague hand-waving vs. precise detail)
- Common hedge phrases (list them: "I think", "perhaps", "it seems")
- Common power phrases (list them: "Here's the truth", "What matters is")

**Warmth & Connection**
- Warmth scale: 1–10
- How do they create intimacy? (shared experience, vulnerability, humor, directness)
- Use of "I" vs. "we" vs. "you" — what's the balance?
- How do they handle disagreement or difficult topics?
- Do they name emotions directly or imply them?

**Personality Markers**
- What are their values? (what themes keep recurring)
- What's their worldview? (optimistic, pragmatic, skeptical, idealistic)
- What's their energy? (high-energy, calm, intense, relaxed)
- Where do they show personality most? (word choice, structure, asides, humor)

**Point of View**
- First person singular ("I")
- First person plural ("we")
- Second person ("you")
- Third person
- Mixed — in what pattern?

---

### Stage 6 — Cross-Sample Synthesis

Compare findings across ALL samples to identify:

**Core Style** — traits present in 70%+ of samples. These are non-negotiable in the stylesheet.

**Situational Adaptations** — traits that shift based on audience/purpose. Note the conditions that trigger the shift.

**Signature Moves** — unique or distinctive patterns that make this writer recognizable. The things a reader would point to and say "that's so [them]."

**Range** — where does the writer flex? What stays fixed vs. what varies?

**Anti-Patterns** — things this writer consistently avoids that other writers commonly do. Just as important as what they do.

---

### Stage 7 — Build the Stylesheet

Compile everything into a comprehensive stylesheet saved as its own file.

The stylesheet MUST include these sections:

```markdown
# [Profile Name] — Style Sheet

> [One-paragraph voice summary: who this writer sounds like, what makes them distinctive]

_Built from [N] samples on [date]._

---

## Quick Reference

**Formality:** [1–10] | **Warmth:** [1–10] | **Confidence:** [1–10] | **Specificity:** [1–10]
**Energy:** [descriptor] | **Humor:** [descriptor] | **POV:** [primary]

---

## Voice DNA

### This writer sounds like...
[2-3 sentence character sketch — as if describing a person you just met]

### Core values that come through
- [value]: [how it shows up in the writing]

### Signature moves
- [move]: [example from samples]

---

## Building Blocks Blueprint

### Article Shape
- Target length: [X–Y words]
- Sections: [N–N] with H2 headers
- Paragraphs per article: [N–N]

### Paragraph Rules
- Sentences per paragraph: [X–Y] (target avg: [Z])
- Words per paragraph: [X–Y] (target avg: [Z])
- One-sentence paragraphs: [frequency — e.g., "1 per section for emphasis"]
- Length rhythm: [pattern — e.g., "medium, short, long, short"]

### Formatting Elements to Use
| Element | How often | How to use it |
|---------|-----------|---------------|
| [e.g., Bulleted lists] | [e.g., 2–3 per article] | [e.g., for feature comparisons, max 5 items] |
| [e.g., Bold text] | [e.g., 3–5 per section] | [e.g., key terms on first use, section leads] |
| [e.g., Block quotes] | [e.g., 1 per article] | [e.g., highlighting a key insight or user quote] |
| [e.g., Em-dashes] | [e.g., frequent] | [e.g., for parenthetical asides and emphasis] |

### Formatting Elements to Avoid
- [Elements absent from all samples — do NOT add these]

### Openings
- [pattern with example]

### Closings
- [pattern with example]

### Section Flow
- [How sections connect, transition style, pacing pattern]

---

## Language Rules

### Vocabulary
- **Use these words/phrases:** [list of signature vocabulary]
- **Avoid these words/phrases:** [list of anti-patterns]
- **Domain terms:** [list]

### Sentences
- Target length: [range]
- Preferred construction: [patterns]
- Punctuation habits: [specifics]

### Rhetorical devices
- [device]: [how they use it, with example]

---

## Tone Calibration

### Default tone
[description]

### How they adjust for...
- **Good news:** [adjustment]
- **Bad news:** [adjustment]
- **Asking for something:** [adjustment]
- **Disagreeing:** [adjustment]

---

## Do / Don't

### Always
- [rule]

### Never
- [rule]

---

## Sample Phrases

Actual phrases pulled from the samples that capture the voice:
1. "[quote]" — [what it demonstrates]
2. "[quote]" — [what it demonstrates]
...

---

## How to Apply This Stylesheet

When writing as this voice:
1. Draft freely first, focusing on content
2. Revise structure to match the Structure Rules
3. Revise language to match the Language Rules
4. Check tone against Tone Calibration
5. Final pass against Do/Don't checklist
6. Read aloud — does it sound like the Sample Phrases?
```

---

### Stage 8 — Review

Present the full stylesheet to the user. Ask:
- Does this capture the voice accurately?
- Anything missing, wrong, or exaggerated?
- What should this stylesheet be named?
- Should any traits be adjusted (e.g., "I want to keep my style but be slightly more formal")?

Iterate on the stylesheet until the user approves.

---

### Stage 9 — Save

1. Save the stylesheet as `${CLAUDE_SKILL_DIR}/stylesheets/[name].md`
2. Add a summary entry to `${CLAUDE_SKILL_DIR}/tone-database.md` under `## Custom Profiles` with a pointer to the full stylesheet file:

```markdown
## [Profile Name]

> [One-sentence voice summary]

**Formality:** [1–10] | **Warmth:** [1–10] | **Confidence:** [1–10]

Full stylesheet: `${CLAUDE_SKILL_DIR}/stylesheets/[name].md`

_Built from [N] samples on [date]._
```

3. Confirm: "Stylesheet '[name]' saved. The writing process will load the full stylesheet and apply it to every article."
