---
name: market-analysis
description: Use when exploring a market, sector, theme, or macro regime top-down with source-cited research — e.g. "analyze the AI semis market", "what's happening in European defense stocks", "explore the lithium thesis", "give me a view on US small caps", "is the consumer rolling over", "map out the Mag 7 vs the rest". Triggers on phrases like "analyze the X market", "explore X theme", "what's the state of X sector", "give me a top-down view", "market analysis", "sector deep-dive", "macro view on X", "X thesis". Produces a structured report with inline footnote citations to primary sources (filings, central-bank releases, official statistics, exchange data, reputable financial press). Distinct from `stock-eval` (single-name fundamentals) and `research-bundle` (single-name multi-skill chain) — this skill is top-down only and always cites sources.
---

# Market Analysis

Top-down, source-cited exploration of markets, sectors, themes, and macro regimes. Every substantive claim earns an inline footnote with URL and access date. Output is structured for a portfolio-level investment view, not single-name diligence.

## Overview

This skill answers questions like:
- "What's actually happening in the AI semis market right now?"
- "Is the lithium thesis still intact?"
- "Are US small caps a buy here?"
- "Map the European defense complex."
- "Macro setup for 2026 H2?"

**Core principle:** the answer is only as good as the sources. Never claim a number or a fact without citing where it came from. The reader should be able to click every footnote and verify.

This skill is explicitly **top-down**. For single-name diligence use `stock-eval`, `fundamental-analysis`, `dcf-valuation`, or chain them via `research-bundle`. This skill sits a level above — it sizes the pond before you pick the fish.

## When to use

Use when the user asks about:
- A market, sector, sub-sector, or thematic basket (semis, defense, lithium, GLP-1, regen ag, datacenters, EM ex-China…)
- A macro regime or rotation question (rates path, USD, oil, recession odds, breadth)
- A flow or positioning question (CTA exposure, retail vs institutional, short interest at sector level)
- A narrative check ("is the AI capex cycle real", "is the consumer rolling over")

Do NOT use when:
- The question is about a single ticker → use `stock-eval` or `research-bundle`
- The question is about a portfolio the user holds → use `portfolio-review`
- The question is about valuing a specific company → use `dcf-valuation`

## Source-citation contract

**Every numeric claim, every named source, every dated event MUST have an inline footnote.**

Format: `[^n]` immediately after the claim, with footnotes collected at the end:

```markdown
US Q1 2026 GDP came in at +2.1% annualized, below consensus of +2.4%[^1].

[^1]: BEA, "Gross Domestic Product, First Quarter 2026 (Advance Estimate)",
      bea.gov/news/2026/gross-domestic-product-first-quarter-2026, accessed 2026-05-15.
```

Source priorities (in order of preference):
1. **Primary**: filings (10-K/10-Q/8-K), central-bank releases (FOMC, ECB, BoE statements), official statistics (BEA, BLS, Eurostat, ONS, BIS), exchange data (NYSE, Nasdaq, LSE, CME)
2. **Industry primary**: trade-body data (SEMI, IEA, USGS, World Steel), company investor decks, conference transcripts
3. **Reputable financial press**: FT, WSJ, Bloomberg, Reuters, The Economist — use when primary not yet available, never as sole citation for a contested claim
4. **Last resort**: analyst notes, sell-side research summaries — must disclose

NEVER cite: forum posts, anonymous Substacks, X/Twitter threads (unless quoting a primary source's verified account), AI-generated summaries.

## Workflow

### Step 1 — Define the scope precisely

Before researching, restate the question in one sentence and confirm with the user. Vague briefs produce sprawling reports. E.g.:
- ❌ "AI market analysis"
- ✅ "Top-down view on US-listed AI semiconductor pure-plays (NVDA, AMD, AVGO, MRVL, ALAB, CRDO) for a 12-month horizon"

### Step 2 — Map the analytical frame

Choose 3–5 of these lenses based on scope:

| Lens | What it answers | Key data to pull |
|---|---|---|
| **Market sizing** | How big, growing how fast | TAM/SAM from primary sources, CAGR, unit vs $ |
| **Supply/demand** | What drives the cycle | Capacity, inventory, utilization, lead times |
| **Pricing power** | Margins durable? | ASP trends, input costs, competitive intensity |
| **Capital flows** | Where is money going | Capex announcements, M&A, VC funding |
| **Positioning** | Who owns it already | Short interest, ETF flows, 13F changes |
| **Macro overlay** | What kills the thesis | Rates sensitivity, FX exposure, regulatory risk |
| **Narrative state** | What is consensus | Sell-side ratings distribution, sentiment indices |
| **Catalysts** | What moves it next 6m | Earnings, policy events, product cycles |

### Step 3 — Source-gather in parallel

Use `firecrawl:firecrawl-search` (NOT WebSearch) — it returns full-page markdown, which is necessary for accurate quotation. Search in parallel, not sequentially:

```
- Central-bank statements + dot plots
- Latest sector ETF flows (XLK, SMH, ITA, LIT, etc.)
- Latest 10-Q/10-K snippets for top 3-5 names
- Trade-body data releases
- 2 reputable press syntheses for cross-check
```

Pull primary sources first. Only consult press as cross-check or for very recent (last 7 days) events not yet in primary data.

### Step 4 — Write the structured report

Standard structure:

```markdown
# <Market/Sector/Theme> — Top-Down View

**Scope:** <one-sentence restatement>
**Horizon:** <e.g. 12 months>
**Bottom line:** <2-3 sentences with the actual view>

## 1. State of play
<What's true today, with footnotes>

## 2. The bull case
<3-5 bullet points, each footnoted>

## 3. The bear case
<3-5 bullet points, each footnoted>

## 4. Positioning & flows
<Who owns it, how crowded, ETF / 13F / short-interest data>

## 5. Catalysts (next 6m)
<Dated upcoming events: earnings, policy meetings, product cycles>

## 6. What would change my mind
<Concrete tripwires — number/event-level, not vibes>

---

## Sources
[^1]: ...
[^2]: ...
```

### Step 5 — Self-check before delivering

Before returning to the user:
- [ ] Every numeric claim has a footnote
- [ ] Every footnote URL is real (not hallucinated) — verify by running `firecrawl-scrape` on at least 2 sampled URLs
- [ ] Access dates are present on all footnotes
- [ ] No claim relies solely on press for a number that has a primary source
- [ ] "Bottom line" is an actual view, not a hedge
- [ ] "What would change my mind" is concrete (numbers/events), not vibes

## Common mistakes

| Mistake | Why bad | Fix |
|---|---|---|
| Using WebSearch instead of firecrawl-search | Snippets aren't enough to quote accurately, may misattribute | Always use `firecrawl:firecrawl-search` for source-bound work |
| Citing AI-generated summaries | Hallucination risk, not verifiable | Cite the primary the summary was built from |
| Bullet lists without footnotes | Reader can't verify, low trust | Every substantive bullet earns a `[^n]` |
| "Consensus expects X" without source | Whose consensus? | Cite the specific FactSet/Bloomberg/IBES table or skip |
| Hedged bottom line ("could go either way") | Useless | Pick a side or explicitly say "no view, here's why" |
| Stale data without flagging | Misleading | If using >90-day-old data, note it in the footnote |

## Cross-references

- For single-name follow-up after market view: chain to `stock-eval` or `research-bundle`
- For valuation work on names that emerge: `dcf-valuation`, `stock-valuation`
- For positioning detail: `short-interest`, `institutional-ownership`, `insider-trading`
- For macro context: `economics-analysis`
- For peer comparison: `competitor-analysis`
- For the actual web research: `firecrawl:firecrawl-search` (always), `firecrawl:firecrawl-scrape` (verification)
