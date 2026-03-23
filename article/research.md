# Research Process

Product-centric research. The product profile is the foundation — this pipeline adds angle-specific depth on top.

**Read `${CLAUDE_SKILL_DIR}/research-profile.md` first.** It defines product sources, competitive sources, and verification rules.

---

## Principles

- **Product profile is the floor, not the ceiling.** It provides baseline facts. This pipeline digs deeper on the specific angle.
- **Go deep, not shallow.** Multiple searches from different angles. Follow every lead.
- **Max tool usage.** Use every search and fetch call needed. Never stop at one query.
- **Product sources first.** Official docs, community, ecosystem — then general sources.
- **Cross-reference everything.** No single-source claims. Verify across independent sources.
- **Feature depth matters.** Don't say "Salesforce has automation." Say which automation tool, which edition, how it works, what it costs, what the limits are.
- **Show your work.** Surface every source URL.

---

## Pipeline

### Phase 0 — Load Product Foundation

Read the product profile from `${CLAUDE_SKILL_DIR}/products/[product].md`. Extract:
- Key facts and claims that are relevant to this article's angle
- Source URLs from the profile that may need rechecking
- Knowledge gaps the profile flagged
- Last updated date — note what may be stale

Read `${CLAUDE_SKILL_DIR}/product-angles.md` for the author's recurring angles. If this article uses a known angle, load the associated framing, competitors, and data points.

### Phase 1 — Scope

Define what this SPECIFIC article needs beyond the product profile:
- **What questions does the angle raise** that the profile doesn't answer?
- **What's changed** since the profile was last updated?
- **What competitive context** does this angle need?
- **What depth is needed?** Feature-level detail? Architecture? Pricing tiers? User workflows?
- **What real-world evidence** would make this article authoritative? (Case studies, benchmarks, user stories)

State the plan: "The product profile covers X. I need to research Y, Z for this angle."

### Phase 2 — Product Deep Dive (Angle-Specific)

Go deep into the specific product features/areas this article covers. For EACH feature or capability mentioned:

**Functional depth:**
1. "[Product] + [feature name] + documentation"
2. "[Product] + [feature name] + how it works"
3. "[Product] + [feature name] + setup / configuration"
4. "[Product] + [feature name] + best practices"
5. "[Product] + [feature name] + limitations / restrictions"
6. "[Product] + [feature name] + [edition/tier] availability"

**Real-world depth:**
7. "[Product] + [feature name] + real world / production"
8. "[Product] + [feature name] + case study / example"
9. "[Product] + [feature name] + tips / tricks / advanced"
10. "[Product] + [feature name] + problems / issues / bugs"
11. "[Product] + [feature name] + workaround"

**Technical depth:**
12. "[Product] + [feature name] + architecture / how it works under the hood"
13. "[Product] + [feature name] + API / developer"
14. "[Product] + [feature name] + performance / scale / limits"
15. "[Product] + [feature name] + integration + [other tools]"

WebFetch official documentation pages for EVERY feature mentioned. Don't paraphrase docs — extract the actual details: field names, option values, step counts, edition requirements, API endpoints, governor limits.

### Phase 3 — Community & User Perspective

What do real users say about this specific angle?

1. "[Product] + [angle/feature] + site:reddit.com"
2. "[Product] + [angle/feature] + site:news.ycombinator.com"
3. "[Product] + [angle/feature] + community forum"
4. "[Product] + [angle/feature] + 'in my experience' OR 'we found that'"
5. "[Product] + [angle/feature] + review + [current year]"
6. "[Product] + [angle/feature] + complaint OR frustration OR wish"
7. "[Product] + [angle/feature] + love OR 'game changer' OR 'best feature'"

Extract real quotes and specific experiences — these give articles authenticity that generic summaries don't.

### Phase 4 — Competitive Context

If the angle involves comparison or positioning:

1. "[Product] vs [Competitor] + [specific area]"
2. "[Competitor] + [equivalent feature] + how it works"
3. "[Product] + migration from [Competitor]" and vice versa
4. "[Product] vs [Competitor] + [current year] + comparison"
5. "[Competitor] + [feature] + limitations" (verify from their own docs)
6. "[Product category] + comparison + [current year]"
7. Neutral comparison sites: G2, Capterra, TrustRadius for this specific area

**Important:** Verify competitive claims from the competitor's own documentation, not from your product's marketing materials.

### Phase 5 — Market & Trend Context

If the angle touches industry trends:

1. "[Product category] + market + [current year]"
2. "[Product category] + trends + predictions"
3. "[Product] + analyst report / Gartner / Forrester"
4. "[Topic of angle] + industry + data / statistics"
5. "[Topic of angle] + [user's industry context]"

### Phase 6 — Verify & Cross-Reference

For EVERY claim that will appear in the article:

- **Product feature claims:** Verified against official docs? Which edition/tier?
- **Pricing claims:** Current as of when? Which currency/region?
- **Performance claims:** Source? Conditions? Reproducible?
- **Competitive claims:** Verified from competitor's own materials?
- **Statistical claims:** Original source found? Sample size? Date?
- **User quotes/experiences:** Real source linked?

Flag anything that:
- Appears in only one source (mark as unverified)
- Contradicts the product profile (the profile may be stale)
- Has changed since the product profile was built

### Phase 7 — Synthesize

Present to the user:

```
## Research Summary

### Product Profile Foundation
- Loaded [product] profile (last updated: [date])
- [N] claims from profile are still current
- [N] claims need updating (list them)

### New Findings for This Angle
- [Finding with feature-level detail] — [source URL]
- [Finding with feature-level detail] — [source URL]

### Feature Deep Dive
- [Feature]: [How it works, which editions, limitations] — [source URL]
- [Feature]: [How it works, which editions, limitations] — [source URL]

### Real User Perspectives
- [Quote or experience] — [source URL]

### Competitive Context
- [Comparison point] — [source URL]

### Conflicting Information
- [Claim A from Source 1] vs. [Claim B from Source 2]

### Gaps
- [What I couldn't find or verify]

### Sources Used
1. [URL] — [what it provided]
...
```

Ask:
> Anything I should dig deeper on? Any features I need more detail on?

---

## Research Depth by Scenario

| Scenario | Min Searches | Min Pages Fetched |
|---|---|---|
| Feature spotlight / how-to | 10–15 | 5–10 |
| Product comparison | 15–25 | 10–15 |
| Deep dive / architecture | 20–30 | 12–20 |
| Industry analysis with product focus | 15–25 | 10–18 |
| Case study / customer story | 10–15 | 8–12 |

When writing about product functionality: **always fetch the actual documentation page.** Paraphrasing product docs from memory is how inaccuracies happen.
