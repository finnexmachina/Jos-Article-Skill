# Product Learning Pipeline

Deep, iterative research on a specific product. For complex products like Salesforce, this means learning the FULL depth of functionality — every major module, every edition difference, every limit and workaround.

The profile becomes the factual backbone of every article. Shallow profiles produce shallow articles.

---

## Input

The user provides:
- A product name (required)
- URLs, docs, or files about the product (optional)
- Specific areas to prioritize (optional)
- Their own expertise level (optional — shapes what to skip vs. dig into)
- **Screenshots from the live product** (optional but highly recommended — see below)

### Screenshots: Why They Matter

Public docs show the marketing version of a product. The real depth — actual UI, field names, settings screens, click paths, real error messages — lives behind the login. Screenshots bridge this gap.

Screenshots go in `${CLAUDE_SKILL_DIR}/screenshots/`, organized by module (e.g., `screenshots/automation/`, `screenshots/admin/`). The user provides them during article requests using the "add another? (yes/no)" loop.

---

## Pipeline

### Stage 1 — Map the Product Surface Area

Before going deep, understand the FULL scope of the product. Complex products like Salesforce aren't one thing — they're platforms with dozens of modules.

1. **Fetch the product's main documentation landing page** — extract the navigation structure. This IS the product map.
2. **Fetch the pricing page** — extract every edition/tier and what's included in each.
3. **Search for "[Product] complete feature list"** and "[Product] product overview / platform overview"
4. **Build a product map:**

```
[Product Name]
├── [Module/Area 1]
│   ├── [Sub-feature A]
│   ├── [Sub-feature B]
│   └── [Sub-feature C]
├── [Module/Area 2]
│   ├── ...
├── [Module/Area 3]
│   └── ...
└── [Platform capabilities]
    ├── [API / Developer tools]
    ├── [Admin / Configuration]
    ├── [Security / Compliance]
    └── [Integrations / Ecosystem]
```

Present the product map to the user:
> Here's the full surface area of [Product]. I'll research each area. Want me to prioritize any specific modules, or go breadth-first?

Also check `${CLAUDE_SKILL_DIR}/screenshots/` for any screenshots already provided from previous articles. Read any relevant images — they add real UI detail that docs don't show.

---

### Stage 2 — Functional Deep Dive (PER MODULE)

**This is the core of the pipeline.** For EACH module/area in the product map, research:

#### A. What it does
- "[Product] + [module] + what is it / overview"
- "[Product] + [module] + documentation"
- WebFetch the official docs page for this module

Extract:
- Purpose and positioning within the product
- Key capabilities (list every one)
- How it relates to other modules

#### B. How it actually works
- "[Product] + [module] + how to use / getting started"
- "[Product] + [module] + setup / configuration / implementation"
- "[Product] + [module] + tutorial / walkthrough"
- WebFetch step-by-step guides

Extract:
- The actual user workflow — steps, clicks, screens
- Configuration options and what they control
- Default settings vs. common customizations
- Dependencies on other modules or setup prerequisites

#### C. Edition/tier differences
- "[Product] + [module] + editions / plans / availability"
- "[Product] + [module] + enterprise vs professional" (or equivalent tier names)
- Check the pricing/editions comparison page for this module

Extract:
- Which editions include this module
- Feature differences between editions for this module
- What's locked behind add-ons or premium tiers
- Free/trial limitations

#### D. Limits, constraints, and gotchas
- "[Product] + [module] + limits / limitations / restrictions"
- "[Product] + [module] + governor limits" (if applicable)
- "[Product] + [module] + known issues / bugs"
- "[Product] + [module] + doesn't support / can't do"
- Search community forums for "[module] + limitation OR frustrating OR workaround"

Extract:
- Hard limits (record counts, API calls, storage, users)
- Soft limits (performance degrades at scale)
- Known issues or bugs
- Missing features users commonly request
- Common workarounds for limitations

#### E. Advanced usage and power features
- "[Product] + [module] + advanced / power user / tips"
- "[Product] + [module] + best practices"
- "[Product] + [module] + automation / customization"
- "[Product] + [module] + API / developer / programmatic"

Extract:
- Features that only experienced users know about
- Automation capabilities
- API access and developer options
- Integration points with other tools
- Non-obvious use cases

#### F. Real user experience
- "[Product] + [module] + site:reddit.com"
- "[Product] + [module] + review OR experience"
- "[Product] + [module] + 'in my experience' OR 'we found'"
- "[Product] + [module] + complaint OR love OR 'game changer'"

Extract:
- What users actually think (not marketing)
- Common praise and complaints
- Real-world performance vs. marketing claims
- Learning curve and onboarding experience

#### G. Competitive comparison for this module
- "[Product] [module] vs [Competitor equivalent]"
- "[Competitor] + [equivalent feature] + how it works"

Extract:
- How competitors handle the same function
- Where the product wins vs. loses for this specific module
- Migration considerations

**Repeat A–G for every major module in the product map.**

For complex products, this means 10–30+ modules. That's correct. Shallow coverage of a deep product is worse than no profile.

---

### Stage 3 — Platform-Level Research

Beyond individual modules, research the platform itself:

**Architecture & Infrastructure**
1. "[Product] + architecture / tech stack / infrastructure"
2. "[Product] + multi-tenant / single-tenant / deployment model"
3. "[Product] + scalability / performance / reliability"
4. "[Product] + uptime / SLA / status history"

**Developer Platform**
5. "[Product] + API documentation"
6. "[Product] + developer tools / SDK / CLI"
7. "[Product] + custom development / extensibility"
8. "[Product] + marketplace / app store / extensions"

**Admin & Operations**
9. "[Product] + administration / admin guide"
10. "[Product] + user management / permissions / roles"
11. "[Product] + data model / schema / object model"
12. "[Product] + backup / data export / portability"

**Security & Compliance**
13. "[Product] + security / encryption / data protection"
14. "[Product] + compliance / SOC2 / GDPR / HIPAA"
15. "[Product] + audit trail / logging"

**Ecosystem**
16. "[Product] + marketplace / third-party apps" — fetch and catalog top apps
17. "[Product] + implementation partners / consultants"
18. "[Product] + community / user groups / events"
19. "[Product] + certification / training / learning path"

---

### Stage 4 — Pricing & Business Model Deep Dive

Don't just list prices — understand the full cost picture:

1. Fetch the pricing page and extract EVERY tier with EVERY included feature
2. "[Product] + pricing + hidden costs / total cost of ownership"
3. "[Product] + add-ons / premium features / upsells"
4. "[Product] + implementation cost / consulting cost"
5. "[Product] + contract / minimum commitment / cancellation"
6. "[Product] + discount / negotiation / enterprise pricing"
7. "[Product] + free tier / trial / freemium limitations"

Build a pricing matrix:
| Feature | Free/Trial | Tier 1 | Tier 2 | Tier 3 | Enterprise | Add-on |
|---------|-----------|--------|--------|--------|-----------|--------|

---

### Stage 5 — Competitive Landscape

1. Identify top 5–7 competitors (search "[Product] alternatives + [current year]")
2. For each competitor:
   - Fetch their website and pricing page
   - Search "[Product] vs [Competitor] + [current year]"
   - Search "[Competitor] + review + [current year]"
   - Note: where they win, where they lose, migration stories both directions
3. Build comparison matrix: features, pricing, strengths, weaknesses, best for

---

### Stage 6 — Third-Party Perspectives

**Reviews & Ratings**
1. Fetch G2, Capterra, TrustRadius pages for the product
2. Extract: overall score, review count, category rankings
3. Extract: most common praise themes, most common complaint themes
4. Note: score trends over time if visible

**Analyst Coverage**
5. "[Product] + Gartner Magic Quadrant / Forrester Wave"
6. "[Product] + analyst report + [current year]"

**Media Coverage**
7. "[Product] + news + [current year]"
8. "[Product] + controversy / criticism / lawsuit"
9. "[Product] + acquisition / IPO / funding"

**People & Culture**
10. "[Product CEO/founder] + interview + [current year]"
11. "[Product] + Glassdoor / employer reviews" (signals company health)
12. "[Product] + roadmap / vision / future"

---

### Stage 7 — Synthesize Into Profile

Compile EVERYTHING into a structured profile:

```markdown
# [Product Name] — Product Profile

_Last updated: [date] | Sources: [count] | Confidence: [high/medium/low]_

---

<!-- SUMMARY SECTION — always loaded by /article -->
<!-- This section is compact enough to load for every article -->

## One-Liner
[What it is in one sentence]

## Overview
[2-3 paragraphs: what it does, who it's for, why it matters, what makes it different]

## Core Details

- **Category:** [Market category]
- **Founded:** [Year]
- **Company:** [Parent company if different]
- **Leadership:** [Key people]
- **Headquarters:** [Location]
- **Funding/Revenue:** [Key financials]
- **Team size:** [Approximate]
- **Customer count:** [If public]
- **Website:** [URL]

## Product Map

[The full module map from Stage 1, with one-line summary per module]

## Key Strengths
- [Strength]: [one-line evidence]

## Key Weaknesses
- [Weakness]: [one-line evidence]

## Competitive Summary
| Competitor | Where [Product] wins | Where they win |
|-----------|---------------------|----------------|

## Pricing Summary
[Tier names, price points, key differences in one table]

<!-- END SUMMARY — everything above is ~200-300 lines max -->

---

<!-- DEEP DIVE SECTIONS — loaded selectively by /article based on the article's topic -->
<!-- Each module section is self-contained so individual ones can be loaded -->

## Functionality Deep Dive

### [Module 1]

**What it does:** [Purpose, positioning]
**Key capabilities:**
- [Capability]: [How it works, what it enables]
...

**Edition availability:**
| Feature | Tier 1 | Tier 2 | Enterprise | Add-on |
|---------|--------|--------|-----------|--------|

**Limits & constraints:**
- [Limit]: [Number/threshold, what happens when hit]

**Power features:**
- [Feature]: [What experienced users know]

**Real user take:**
- [What users love] — [source]
- [What users hate] — [source]

**vs. Competitors:**
- [Competitor]: [How they compare on this module]

### [Module 2]
[Same structure]

### [Module N]
[Same structure — EVERY major module gets this treatment]

---

## Platform Details

### Architecture
[How it works under the hood]

### Developer Platform
[APIs, SDKs, extensibility, marketplace]

### Admin & Operations
[User management, data model, configuration]

### Security & Compliance
[Certifications, encryption, audit capabilities]

---

## Pricing

### Edition Comparison
[Full pricing matrix]

### Total Cost of Ownership
- License: [cost]
- Implementation: [typical range]
- Ongoing admin: [typical cost]
- Add-ons commonly needed: [list with costs]
- Training: [typical investment]

### Contract Details
[Minimums, commitment periods, negotiation notes]

---

## Ecosystem

### Top Marketplace Apps
- [App]: [What it does, rating, installs]

### Implementation Partners
- [Partner type]: [What they do, typical cost]

### Community
- [Forum/community]: [Size, activity, quality]

### Certification Path
- [Cert]: [What it proves, difficulty, value]

---

## Competitive Landscape

### Comparison Matrix
| Dimension | [Product] | [Competitor 1] | [Competitor 2] | [Competitor 3] |
|-----------|----------|----------------|----------------|----------------|
| Best for | | | | |
| Pricing | | | | |
| Ease of use | | | | |
| Customization | | | | |
| Integrations | | | | |
| Support | | | | |

### Head-to-Head Details
[Detailed comparison per competitor]

---

## Sentiment & Reputation

### Review Scores
| Platform | Score | Reviews | Trend | Source |
|----------|-------|---------|-------|--------|

### What Users Love (with sources)
- [Theme]: [Details] — [URL]

### What Users Criticize (with sources)
- [Theme]: [Details] — [URL]

---

## Recent Developments

- [Date]: [Event] — [source URL]

---

## Narrative Angles

Potential article angles identified during research:

1. **[Angle]:** [What makes it interesting, evidence found]
2. **[Angle]:** [What makes it interesting, evidence found]
...

---

## Raw Source Index

| # | Source | URL | What it provided |
|---|--------|-----|-----------------|
| 1 | | | |
...

---

## Knowledge Gaps

- [What couldn't be found or verified]
- [Areas that need deeper research]
- [Information that may be outdated]

---

## Iteration Log

| Date | What was updated | Sources added |
|------|-----------------|---------------|
| [date] | Initial profile | [N] sources |
```

---

### Stage 8 — Review & Iterate

Present the profile to the user:

> Here's the full profile for [Product] — [N] sources across [N] modules.
>
> **Depth check:**
> - [N] modules covered in full detail
> - [N] modules at surface level (need more research)
> - [N] known gaps
>
> Want me to:
> - Go deeper on any specific module?
> - Research additional competitor comparisons?
> - Dig into a specific use case or industry vertical?
> - Fill in any of the knowledge gaps?

**This is iterative.** The user can:
- Request deeper dives on specific modules (loops back to Stage 2 for that module)
- Come back later and say "update the profile" — refresh stale data
- Say "add [new module/feature]" — extend the profile as the product evolves

---

### Stage 9 — Save

Save to `${CLAUDE_SKILL_DIR}/products/[product].md`

Confirm:
> Product profile for '[Product]' saved.
> - [N] total sources
> - [N] modules with full deep-dive coverage
> - [N] competitors mapped
> - Last updated: [date]
>
> This profile is now the foundation for every article about [Product]. Run `/article` to start writing.

---

## How Products Get Used in Articles

When `/article` runs:

1. Product profile is loaded as the **mandatory foundation**
2. Article research builds on the profile — adds angle-specific depth
3. Writing process verifies claims against the profile + official docs
4. Product accuracy check ensures feature names, editions, and limits are correct
5. Original sources from the profile are cited in the article

The profile provides:
- Accurate feature-level detail (names, workflows, editions, limits)
- Real user perspectives and sentiment
- Competitive positioning with evidence
- Pricing and business model context
- Narrative angles the author has identified
