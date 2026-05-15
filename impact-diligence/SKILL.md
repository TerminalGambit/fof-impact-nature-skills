---
name: impact-diligence
description: Use when evaluating a fund manager, direct deal, or portfolio company against impact criteria — especially for impact-aligned, regenerative, or natural-capital transactions in VC, PE, real assets, or fund-of-funds contexts. Applies the Impact Management Project (IMP) five-dimensions framework, suggests IRIS+ metric IDs from the GIIN catalog, maps to UN SDG targets, and runs an additionality stress-test. Output is structured for IC memos and LP-facing reports.
---

# Impact diligence — IMP five dimensions + IRIS+ mapper

## When to use this skill

Trigger this skill when any of the following appear in the conversation:
- A fund manager's impact thesis is being assessed
- A direct deal or co-invest opportunity claims impact alignment
- A portfolio company's impact report needs to be evaluated for credibility
- A new investment is being scored against an impact lens (regen, climate, biodiversity, livelihoods, etc.)
- The user asks "is this real impact?" or "what's the actual impact thesis here?"

If the conversation is about *measuring already-deployed impact* (vs evaluating a prospective deal), still use this — the framework applies symmetrically.

## What this skill produces

A structured impact diligence assessment with five components:

1. **IMP five-dimensions scorecard** (What / Who / How Much / Contribution / Risk)
2. **IRIS+ metric suggestions** — concrete metric IDs from the GIIN catalog that match the deal's impact claims
3. **SDG mapping** — specific SDG *targets* (not just goals), with confidence levels
4. **Additionality stress-test** — three questions the investor must answer
5. **Verification quality assessment** — how the manager is measuring, and whether it's credible

## The IMP five dimensions — the core framework

The Impact Management Project (IMP) framework is the de facto language of institutional impact investing. Every dimension must be addressed for an impact claim to be credible.

### 1. WHAT — what outcome is occurring, and how important is it?

Questions to answer:
- What specific outcome does this investment produce? (Not "improve health" — *which* health outcome, measured *how*?)
- Is the outcome positive, negative, or both? (Most real interventions have both.)
- Is the outcome valued by the stakeholders experiencing it?
- Is it aligned with the SDGs / Paris Agreement / Kunming-Montreal Global Biodiversity Framework?

Red flags:
- Outcomes described only as activities or outputs ("planted 1M trees" tells you nothing about survival, ecosystem services, or beneficiary outcomes)
- No mention of negative outcomes — every real intervention has trade-offs
- Outcomes are sponsor-defined but never validated with stakeholders

### 2. WHO — who experiences the outcome?

Questions to answer:
- Specifically which stakeholders (geography, demographics, baseline conditions)?
- How underserved are they? (IMP uses an A/B/C/D classification roughly matching expected counterfactual conditions)
- Is the data disaggregated (gender, age, income decile, geography)?

Red flags:
- "Communities" or "smallholders" used without specifics
- No baseline data
- Aggregate metrics that hide distribution (e.g., average income went up but median stayed flat)

### 3. HOW MUCH — how much of the outcome occurs?

Three sub-dimensions:
- **Scale:** how many stakeholders experience the outcome
- **Depth:** how significant the change is *per stakeholder* (degree)
- **Duration:** how long the change lasts

Red flags:
- Reports scale (number reached) but not depth (per-stakeholder change)
- No durability assessment — does the outcome persist after the investment exits?
- Headline numbers without unit economics

### 4. CONTRIBUTION — would this have happened anyway?

The counterfactual question. Three lenses:
- **Enterprise contribution:** does the investee organization cause the outcome, or just associate with it?
- **Investor contribution:** does this specific investor add anything the enterprise couldn't get elsewhere? (Patient capital? Networks? Expertise? Concessionality?)
- **Stakeholder contribution:** would the stakeholders have achieved the outcome through another route?

This is the most contested dimension and the most often hand-waved.

Red flags:
- No counterfactual analysis at all
- Counterfactual assumes the investee wouldn't have raised capital from anyone (rarely true)
- Investor-contribution argument relies entirely on "we have an impact thesis" (so do many others now)

### 5. RISK — what could prevent the outcome?

Nine types of impact risk (per IMP):
1. **Evidence risk** — outcome may not occur because the evidence base is weak
2. **External risk** — outcome may not occur because of factors outside the investee's control
3. **Stakeholder participation risk** — stakeholders may not engage as needed
4. **Drop-off risk** — outcome reverses after intervention
5. **Efficiency risk** — outcome occurs but at higher cost than alternatives
6. **Execution risk** — investee fails to implement
7. **Alignment risk** — investee's incentives drift away from the impact thesis
8. **Endurance risk** — investee can't sustain the activities long enough
9. **Unexpected impact risk** — negative impact materializes that wasn't anticipated

For a credible impact thesis, the top 3–4 risks should be named and a mitigation should exist.

## IRIS+ metric mapping

IRIS+ (Impact Reporting and Investment Standards Plus, from the GIIN) is the most-used catalog of impact metrics in institutional investing. ~600 metrics, organized by Impact Category → Strategic Goal → Core Metrics Set.

**How to use:** Once the WHAT and HOW MUCH dimensions are clear, suggest 3–5 IRIS+ metric IDs the manager *should* be reporting. Format: `[IRIS+ ID] — [Metric name]`.

Example mapping for a regenerative ag fund:
- `PI8330` — Land Directly Controlled: Sustainably Managed
- `OI1118` — Greenhouse Gas Emissions Reduction (CO2e MT)
- `PI3389` — Smallholder Suppliers
- `OD8060` — Soil Organic Carbon Change (if measuring outcomes)

The asset folder includes a CSV of the most relevant IRIS+ categories for the user's typical deal types (regen, natural capital, climate, real assets). See `assets/iris-plus-relevant.csv` — drop in the full GIIN catalog if needed.

## SDG mapping — targets, not just goals

Don't map to "SDG 15: Life on Land." Map to specific *targets* like "SDG 15.3: combat desertification, restore degraded land and soil." The targets are where the meaningful claims live.

Provide confidence levels:
- **High** — direct measurable contribution
- **Medium** — plausible contribution but not directly measured
- **Aspirational** — alignment in narrative only

Be willing to say "no SDG target maps cleanly" when that's true — better than forcing it.

## Additionality stress-test — three questions

If a manager can't answer these, the impact thesis is weak:

1. **Financial additionality:** Would this enterprise have raised capital on the same terms from a non-impact investor? If yes, what does the impact capital add?
2. **Behavioral additionality:** Does the impact capital change the enterprise's behavior (governance, reporting, target-setting, mission lock)?
3. **Outcome additionality:** Would the outcome have occurred without this enterprise existing? (Hardest test — often we can only argue *acceleration* not *additionality*.)

## Verification quality — the credibility ladder

Rank the manager's MRV (measurement, reporting, verification) approach:

1. **Self-reported, no third party** — lowest credibility, useful only for direction
2. **Self-reported with third-party review of methodology** — middling
3. **Outputs verified by third party (e.g., B Lab GIIRS)** — good
4. **Outcomes verified by independent third party with site-level sampling** — strong
5. **Outcomes verified + peer-reviewed publication / regulatory standard** — gold standard

Most impact funds today sit at level 2–3. Level 4–5 is where the genuinely defensible theses live.

## Output structure for memos

When producing the diligence assessment, format as:

```
## Impact Diligence Assessment — [Fund / Deal Name]

### IMP Scorecard
- WHAT: [outcome description] — [score: clear / partial / vague]
- WHO: [stakeholders, baseline] — [score]
- HOW MUCH: [scale / depth / duration] — [score]
- CONTRIBUTION: [counterfactual] — [score]
- RISK: [top 3 risks + mitigations] — [score]

### IRIS+ Metrics (suggested)
- [Metric ID] — [Name] — [Why relevant]
- ...

### SDG Mapping
- SDG X.Y — [confidence: High / Medium / Aspirational] — [evidence]

### Additionality Stress Test
- Financial: [answer]
- Behavioral: [answer]
- Outcome: [answer]

### Verification Quality
- Current level: [1-5]
- What would move them up a level: [specific recommendation]

### Bottom Line
- Impact thesis strength: [Strong / Adequate / Weak]
- Top 2 things to push on in next conversation: [specific]
- Memo language recommendation: [precise phrasing for IC]
```

## When NOT to use this skill

- For pure financial analysis with no impact dimension — use the financial-analysis skills instead.
- For carbon-credit-specific evaluation — use `carbon-credit-quality`.
- For TNFD / nature-related risk specifically — use `tnfd-leap`.
- For taxonomy disambiguation in regen ag — use `regen-glossary` first, then return to this.

## References

The supporting `assets/` folder contains:
- `imp-five-dimensions.md` — full IMP framework reference
- `iris-plus-relevant.csv` — curated IRIS+ metrics for typical deal types
- `sdg-targets-reference.md` — full SDG targets list (not just goals)

If those files aren't present, the skill still works from the body above but with reduced specificity on metric IDs.
