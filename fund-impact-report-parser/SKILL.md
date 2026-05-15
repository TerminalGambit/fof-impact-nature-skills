---
name: fund-impact-report-parser
description: Use when reading one or more annual impact reports from underlying funds (Bridges, Generation, KKR Global Impact, TPG Rise, Acumen, Root Capital, Trill, Sustainable Land Bond, and similar) and the goal is to extract a comparable structured row per fund for an LP / fund-of-funds allocator. Parses each report into theory-of-change, IRIS+ metric IDs used, IMP five-dimensions coverage, verification method, additionality claims, SDG targets, negative impact disclosure, regen / natural-capital specifics, carbon claims, and verification gaps. Output is a per-fund row designed to assemble side-by-side across N managers for an IC packet or LP-facing impact report. Chains to `impact-diligence` for IMP framework rigor and to `regen-glossary` for regen vocabulary precision.
---

# Fund impact report parser — comparability row builder

## When to use this skill

Trigger when any of these apply:
- The user has one or more annual fund impact reports (PDF, web page, or extracted text) and wants a comparable extraction across managers
- The user is assembling an IC packet or LP-facing impact report that aggregates across underlying funds
- A manager's impact report needs to be parsed into the same schema the LP already uses for its other funds
- The user says "extract the comparability row," "build the cross-manager table," "parse this impact report," or similar

If the user is *evaluating a prospective deal* rather than reading a backward-looking report, prefer `impact-diligence` directly. This skill is for retrospective parsing.

## What this skill produces

One structured row per fund, with ten fields, plus a small block of qualitative notes. Rows are designed to stack into a comparison table across managers. Output format is either markdown table rows or JSON objects (ask the user which).

The ten fields, in order:

1. **Theory of Change** — inputs → activities → outputs → outcomes → impacts, with specifics
2. **IRIS+ metrics reported** — IDs the fund actually uses (cross-ref `impact-diligence/assets/iris-plus-relevant.csv`)
3. **IMP five-dimensions coverage** — What / Who / How Much / Contribution / Risk (explicit / partial / absent)
4. **Verification method** — self-reported / third-party-reviewed / third-party-verified / outcomes-verified / peer-reviewed
5. **Additionality claims** — financial / behavioral / outcome additionality, with the counterfactual argument
6. **SDG alignment** — specific *targets* (e.g., 15.3), with confidence: High / Medium / Aspirational
7. **Negative impact disclosure** — does the report disclose trade-offs and unintended consequences?
8. **Regen / natural-capital specifics** — SOC, agroecology, agroforestry ha, biodiversity, water, smallholder livelihoods
9. **Carbon claims** — verified credits (Verra / Gold Standard / ACR / CAR) separated from "estimated carbon impact" narratives
10. **Verification gaps** — what is claimed but unverified

## Parsing approach

### Step 1 — Identify the report's structure

Most institutional fund impact reports follow one of a few archetypes. Skim the table of contents first and locate:

- **Theory of change section** (sometimes labeled "impact model," "logic model," or "framework")
- **Portfolio metrics dashboard** (the headline numbers)
- **Methodology / measurement appendix** (where the real signal lives — IRIS+ codes, MRV approach, third-party assurances)
- **Case studies** (anecdotal — useful for cross-checking the dashboard, not for the row)
- **Limitations / methodology caveats** (often buried — read this first, not last)

See `assets/exemplar-report-structures.md` for typical section layouts of major managers' reports so you know where to look.

### Step 2 — Extract each of the ten fields

For each field, capture *what the report says* and *what's missing*. The parser's value is in surfacing the gap.

**Theory of Change.** Look for an explicit ToC diagram or paragraph. If only an "impact thesis" exists, reconstruct the implied chain: capital deployed (inputs) → portfolio company activities → measured outputs → claimed outcomes → asserted impacts. Note which links are evidenced and which are assertion.

**IRIS+ metrics.** Search the report for "IRIS+", "IRIS", or any metric ID matching the pattern `[A-Z]{2}\d{4}` (e.g., `PI8330`, `OI1118`, `OD8060`). Many funds reference IRIS+ in the methodology appendix only. Cross-reference each cited ID with `impact-diligence/assets/iris-plus-relevant.csv` to confirm correct usage. Flag IDs cited but not actually reported on.

**IMP five-dimensions.** For each dimension (What, Who, How Much, Contribution, Risk), mark:
- **explicit** — the report names the dimension and addresses it
- **partial** — the dimension is addressed but not named, or addressed at portfolio level only
- **absent** — not addressed

Contribution and Risk are the most-skipped. If the report has no counterfactual reasoning and no impact-risk inventory, mark both absent — don't be charitable.

**Verification method.** Locate the assurance statement. Map to one of five levels (from `impact-diligence` credibility ladder):
1. Self-reported, no third party
2. Self-reported with third-party review of methodology
3. Outputs verified by third party (e.g., B Lab, GIIRS, BlueMark verification)
4. Outcomes verified by independent third party with site-level sampling
5. Outcomes verified + peer-reviewed publication or regulatory standard

Note the assurance provider by name (BlueMark, KPMG, PwC, Tideline, etc.) and the scope of assurance (limited vs reasonable, methodology vs data).

**Additionality claims.** Look for explicit financial / behavioral / outcome additionality reasoning. Most reports assert investor contribution without testing it. Capture the exact counterfactual argument used, or note its absence. Beware "we provided patient capital" as a stand-alone claim — push for specifics.

**SDG alignment.** Map only to specific *targets* (e.g., 15.3, 2.4, 8.7), not goals. If the report names only goals (SDG 13, SDG 15), mark all targets as "Aspirational" unless evidence supports more. Use the targets list in `impact-diligence/assets/sdg-targets-reference.md`.

**Negative impact disclosure.** Search for "trade-offs," "unintended," "negative," "limitations," "harm," "risk of." Most reports omit this entirely. A report that names two or three real trade-offs is meaningfully more credible than one that names none.

**Regen / natural-capital specifics.** For funds with land-based theses, extract:
- SOC measurements (with depth, methodology, baseline year, change over period)
- Agroecology indicators (FAO 10 elements language, if used)
- Agroforestry hectares *with* tree density (stems/ha) and species composition — flag if density is missing
- Biodiversity metrics (species counts, habitat ha, structural diversity, eDNA)
- Water outcomes (infiltration, retention, watershed-scale outcomes vs farm-scale)
- Smallholder livelihoods (income change, with baseline + comparison group)

Apply `regen-glossary` for vocabulary precision — flag any conflation (regenerative used to mean sustainable, no-till claimed as regenerative without diversification, etc.).

**Carbon claims.** Separate cleanly:
- **Verified credits issued** — registry (Verra / Gold Standard / ACR / CAR / Plan Vivo), methodology ID (e.g., VM0042, CDM AR-AMS0007), vintage, tCO2e, retired vs unretired
- **Estimated / modeled carbon impact** — model used, assumptions, whether internal or third-party-modeled
- **Avoided emissions claims** — counterfactual baseline (this is where most claims weaken)

If the report blurs verified and estimated carbon, flag it explicitly.

**Verification gaps.** List every claim made without verification. Common patterns:
- Outcomes asserted that are actually outputs ("X farmers trained" is an output, not an outcome)
- Beneficiary counts without baselines
- Carbon estimates without registry credits
- Biodiversity claims without ecological survey
- Livelihood claims without disaggregated income data

### Step 3 — Assemble the row

Use the output template below. Keep each field terse — this row needs to sit next to four to ten others.

## Output template — single fund row

```
## Fund: [Manager + vintage]

**Theory of Change.** [1–2 sentences capturing inputs → activities → outputs → outcomes → impacts; flag any link that is assertion rather than evidence.]

**IRIS+ metrics reported.** [comma-separated IDs cited in the report] — [count actually reported on, vs cited]

**IMP coverage.** What: [explicit/partial/absent] · Who: [...] · How Much: [...] · Contribution: [...] · Risk: [...]

**Verification.** Level [1–5] — [assurance provider] — [scope: limited/reasonable; methodology/data; output/outcome]

**Additionality.** Financial: [claim or absent] · Behavioral: [...] · Outcome: [...]

**SDG targets.** [target IDs] — confidence: [High/Medium/Aspirational each]

**Negative impact disclosure.** [yes/partial/no] — [if yes, what trade-offs named]

**Regen / natural capital.** SOC: [...] · Agroforestry: [ha + density or "density unreported"] · Biodiversity: [...] · Water: [...] · Smallholders: [...]

**Carbon claims.** Verified credits: [registry / methodology / tCO2e or "none"] · Estimated: [scope + model] · Avoided emissions: [yes/no + counterfactual]

**Verification gaps.** [bullet list — every claim made without verification]

**Top 3 IC-relevant flags.** [the three things the allocator should raise with the GP]
```

## Output template — cross-manager comparison

When the user provides multiple reports, also produce a compact markdown table after the individual rows:

| Fund | ToC explicit? | IRIS+ IDs | IMP all 5? | Verif level | Negatives disclosed? | Carbon: verified / estimated | Top flag |
|---|---|---|---|---|---|---|---|
| ... | ... | ... | ... | ... | ... | ... | ... |

Ask the user whether they want JSON output as well for downstream tooling. If yes, mirror the per-fund template into a JSON object per fund.

## Disposition — what this skill is *not*

This is a parser, not a scorecard. Do not recommend funds as good or bad. Do not weight or rank. The LP will make those judgments using this skill's output plus their own diligence.

Be skeptical by default. The skill's value is identifying what is *claimed* vs what is *verified* — not validating the manager's narrative. If the report is well-written and full of strong language but thin on verification, the row should reflect that. Credulity here destroys downstream IC value.

## Chains to

- `impact-diligence` — when the user wants to move from parsing to evaluation (IMP scoring, additionality stress-test, IC recommendation language)
- `regen-glossary` — whenever the report uses regenerative / agroecology / agroforestry / holistic management language; check definitions before accepting them
- `fund-of-funds-diligence` — for the LP-level portfolio aggregation question (concentration, overlap, vintage diversification across impact theses)

## When NOT to use this skill

- For evaluating a prospective deal that has no annual report yet — use `impact-diligence`.
- For taxonomy-only questions on regen vocabulary — use `regen-glossary` directly.
- For carbon-credit-specific quality assessment beyond the parsed claim — use a carbon-credit-quality skill if available.
- For TCFD / TNFD / SFDR regulatory-disclosure parsing — those have their own schemas and shouldn't be forced into this one.

## References

The supporting `assets/` folder contains:
- `exemplar-report-structures.md` — typical section layouts of major fund impact reports so the parser knows where to look

The skill also relies on assets from `impact-diligence`:
- `iris-plus-relevant.csv` — for IRIS+ ID cross-reference
- `sdg-targets-reference.md` — for SDG target mapping
- `imp-five-dimensions.md` — for IMP coverage assessment

If those assets are unavailable, the skill still functions from the body above with reduced specificity on metric IDs and target codes.
