---
name: carbon-credit-quality
description: Use when assessing voluntary carbon market (VCM) credits — either as the asset being financed (carbon project developers, nature-based solutions funds, ARR/REDD+/ALM/blue-carbon/DAC projects) or as a claim inside a portfolio company's net-zero narrative. Applies the ICVCM Core Carbon Principles, evaluates methodology and registry, runs the five quality questions (additionality, permanence, leakage, double counting, MRV), flags project-type-specific weaknesses, and cross-references public rating-agency assessments. Output is structured for IC memos and LP-facing reports.
---

# Carbon credit quality — ICVCM CCPs + methodology / registry / project-type assessment

## When to use this skill

Trigger this skill when any of the following appear in the conversation:
- A fund or direct investment is a carbon project developer, nature-based solutions vehicle, or removals platform
- A portfolio company is using purchased credits as part of a net-zero or "carbon-neutral" claim
- A manager's impact thesis depends materially on credit issuance, sale, or appreciation
- The user asks "are these credits real?", "what's the quality of this vintage?", or "can we underwrite this offtake?"
- Diligence touches Article 6, ITMOs, corresponding adjustments, or compliance-VCM linkages

If carbon credits are tangential (e.g., a small offset purchase in an otherwise non-climate deal), still run the five quality questions but skip the full CCP scorecard.

## What this skill produces

A structured carbon-credit quality assessment with five components:

1. **ICVCM CCP scorecard** — 10 Core Carbon Principles, scored pass / partial / fail / unknown
2. **Methodology assessment** — methodology ID, vintage, known weaknesses, version currency
3. **Registry assessment** — issuing registry, its track record, governance flags
4. **Five quality questions** — additionality, permanence, leakage, double counting, MRV
5. **Project-type-specific concerns** — calibrated to ARR, IFM, REDD+, ALM, blue carbon, DAC, cookstoves, methane, renewables
6. **Final disposition** — high quality / moderate / low / reject, with the specific reasons

## The ICVCM Core Carbon Principles — the master framework

The Integrity Council for the Voluntary Carbon Market (ICVCM) publishes the Core Carbon Principles (CCPs) as the global benchmark for VCM quality. As of writing, ICVCM assesses methodology categories (not individual projects) for CCP-eligibility. A "CCP-eligible" methodology is necessary but not sufficient for a high-quality credit — the project still has to be diligenced.

The 10 CCPs, grouped:

**Governance (1–3)**
1. **Effective governance** — registry has transparent rules, public registry of issuances and retirements, conflict-of-interest controls.
2. **Tracking** — each unit is uniquely serialised and trackable from issuance to retirement; no cross-registry double-issuance.
3. **Transparency** — methodology documents, project documents, validation/verification reports, monitoring reports all publicly available.

**Emissions impact (4–7)**
4. **Robust independent third-party validation and verification** — accredited VVB (validation/verification body), with rotation and conflict controls.
5. **Additionality** — the GHG outcome would not have occurred without the carbon revenue.
6. **Permanence** — emission reductions/removals are permanent, or non-permanent risks are addressed via buffer pool, insurance, or reversal compensation.
7. **Robust quantification** — conservative baselines, accurate MRV, discounts for uncertainty and leakage.

**Sustainable development (8–10)**
8. **No double counting** — single issuance, single claim, single retirement; corresponding adjustments under Article 6 where applicable.
9. **Sustainable development benefits and safeguards** — alignment with SDGs, do-no-harm safeguards, FPIC for projects affecting indigenous peoples and local communities (IPLCs).
10. **Net-zero transition contribution** — the project type is consistent with a 1.5°C pathway (excludes activities that lock in fossil infrastructure).

Score each CCP **pass / partial / fail / unknown**. "Unknown" is a finding — push back for documentation.

## Methodology assessment

Three things matter: which methodology, which version, and which known weaknesses apply.

**Vintage rule of thumb:** newer methodology versions are generally tighter. A project registered under an older methodology version (e.g., VCS VM0007 pre-2020 REDD+ projects) carries more baseline-inflation risk than the same project under a current ART-TREES jurisdictional approach.

Common methodologies the user is likely to encounter:

- **VM0042** (Verra) — Improved Agricultural Land Management. The dominant soil-carbon methodology. Concerns: model-heavy MRV, additionality testing in regions where regen practices were already spreading.
- **VM0048** (Verra) — REDD+ avoided deforestation, replaces the older VM0006/VM0007/VM0009/VM0015 family with a consolidated, jurisdictional-data-anchored approach. Concerns: still relatively new; legacy VM0007 projects transitioning to VM0048 may have different baselines and credit volumes.
- **AR-ACM0003** (CDM legacy, used in VCS) — Afforestation/reforestation on degraded land. Concerns: monoculture plantation risk, leakage from displaced land users, permanence given fire/disease risk.
- **VM0007** (Verra, legacy REDD+) — Most-criticised REDD+ methodology family for baseline inflation. New issuances should be diminishing post-VM0048.
- **VM0033** (Verra) — Tidal wetland and seagrass restoration (blue carbon). Concerns: monitoring difficulty subsurface, salinity/sediment variability.
- **CDM AMS-II.G** and ICS methodologies for cookstoves (also Gold Standard TPDDTEC) — Concerns: usage-rate assumptions, fuel-substitution heterogeneity, double-counting with national NDCs.
- **ACM0001 / CDM landfill gas** — Generally robust on additionality test, but check whether host-country regulation has since made flaring mandatory (kills additionality).
- **Various renewable energy methodologies (ACM0002, etc.)** — In the VCM, grid-connected renewables almost universally fail additionality today; most credible registries have stopped issuing for them in most geographies. Treat with strong skepticism.

See `assets/methodology-flags.md` for a longer reference list. If the methodology isn't in the assets file, ask for the methodology ID and version explicitly — never accept "Verra-verified" as sufficient detail.

## Registry assessment

Strengths and weaknesses by registry — see `assets/registry-comparison.md` for the full table. Headline points:

- **Verra (VCS)** — largest by volume; broadest methodology coverage; has issued credits later flagged as low-quality (especially legacy REDD+). Recent reforms (VM0048, methodology consolidation) are improvements but legacy stockpile is mixed.
- **Gold Standard** — smaller, generally tighter project review, strong SDG-impact framing, popular for cookstoves and water projects. Premium pricing reflects the brand.
- **ART/TREES** — jurisdictional REDD+ (national or sub-national scale), aligned with LEAF Coalition demand, structurally avoids many baseline-inflation criticisms of project-scale REDD+. Volumes still ramping.
- **ACR (American Carbon Registry)** — US-centric; strong on methane (livestock, landfill) and IFM in US contexts.
- **CAR (Climate Action Reserve)** — US/Mexico focus; respected on US forestry and ODS destruction.
- **Plan Vivo** — smallholder and community-led projects; outcomes credible but volumes small and ex-ante issuance model carries different risk profile.

Always check: registry of issuance + serial number + retirement status. "Verra-listed" without a serial number is not verification.

## The five quality questions

These map onto CCPs 5–8 but operationalise them for diligence.

### 1. Additionality
Would the project have happened without carbon-credit revenue? Three tests:
- **Financial:** is carbon revenue >5% of project IRR? If not, additionality is questionable.
- **Regulatory:** is the activity already mandated by law in the host jurisdiction?
- **Common-practice:** is this activity now standard practice in the region? (e.g., a no-till project in a region where most farmers have already adopted no-till)

Red flag: additionality argued only via "barriers" narrative without financial or counterfactual data.

### 2. Permanence
How long will the carbon stay sequestered? For nature-based projects, the answer is "decades to centuries with risk." Look for:
- **Buffer pool contribution** — what % of issued credits go to the registry's risk-pool reserve? VCS buffer is typically 10–60% depending on AFOLU non-permanence risk score.
- **Reversal monitoring** — how is reversal detected (remote sensing cadence, ground-truth, third-party)?
- **Reversal compensation** — what happens if there's a fire, pest outbreak, harvest, or political change? Is there insurance? A backstop guarantor?
- **Crediting period** — typically 20–40 years; some projects renew. A 100-year permanence claim from a 20-year crediting period is a leap.

Red flag: soil carbon with permanence claimed via a single soil core every 5 years. Soil carbon is the most reversible nature-based pool — a single tillage event can release years of accumulation.

### 3. Leakage
Does the project shift emissions elsewhere?
- **Activity-shifting leakage** — e.g., loggers move from a REDD+ project to an unprotected forest 50 km away.
- **Market leakage** — e.g., reducing timber output in one region raises timber prices and incentivises more harvest elsewhere.
- **Discount rate** — what leakage deduction is applied? Typical 10–40% depending on methodology and project type.

Red flag: leakage assumed to be zero, especially for IFM and REDD+ projects in regions with active commercial logging or agricultural frontiers.

### 4. Double counting
Three sub-issues:
- **Double issuance** — same activity credited under two registries (rare but historically documented; cross-registry checks now standard).
- **Double claiming** — the host country counts the reduction toward its NDC *and* a corporate buyer claims it. Under Article 6.2, a corresponding adjustment (CA) by the host country prevents this. Most VCM credits today are *not* CA-backed.
- **Double use** — the same retired credit referenced in two corporate claims.

For credits used in cross-border net-zero claims, ask: is there a corresponding adjustment? If not, the claim is "contribution-style," not equivalent to the buyer's own emission reduction.

### 5. MRV (measurement, reporting, verification)
- **Measurement:** remote sensing (e.g., Landsat / Sentinel for forest cover, ESA Biomass for AGB) vs ground truth (plots, soil cores, eddy covariance towers) vs modelling (DNDC, Roth-C). Best practice combines all three.
- **Reporting:** monitoring report frequency. Annual is standard; some methodologies allow longer cycles.
- **Verification:** by an accredited VVB; auditor rotation; site visits vs desk review.

Red flag: 100% model-based MRV with no ground truth; or ground truth at a tiny sample (e.g., 5 soil cores for a 50,000 ha project).

## Project-type assessment — calibrate rigor by type

Different project types have different dominant failure modes. Tune diligence accordingly.

- **ARR (afforestation / reforestation / revegetation)** — Permanence (fire, harvest), monoculture biodiversity concerns, additionality if land was already trending to natural regeneration, leakage from displaced land users. Check species mix, tenure, fire management.
- **IFM (improved forest management)** — Baseline gaming (was the harvest schedule realistic counterfactually?), leakage to other parcels, "paper additionality." Look for credible counterfactual harvest plans and FSC/SFI cross-references.
- **REDD+ (avoided deforestation)** — Baseline setting is the central issue. Project-scale baselines have been widely criticised; jurisdictional (ART-TREES) approaches address this structurally. Check whether project uses static reference period, dynamic baseline, or jurisdictional anchor.
- **ALM (agricultural land management, including soil carbon)** — Additionality (is regen ag already spreading?), permanence (soil pools are reversible), MRV cost (soil sampling is expensive). VM0042 is the dominant methodology; look for sampling design, model calibration, and uncertainty discounts.
- **Blue carbon (mangroves, seagrass, salt marsh)** — Genuinely high carbon density; but subsurface MRV is hard, tenure / community-rights are usually complex, and sea-level rise threatens permanence. VM0033 is the key methodology.
- **DAC / CCS / engineered removals** — Higher per-tonne cost; permanence usually strong (geological storage measured in millennia); MRV is industrial-process measurement, generally robust. Check energy source for the capture process (if fossil-powered, lifecycle accounting matters).
- **Cookstoves** — Usage-rate assumption is the central driver of credit volumes. Look for surveys with sensored stoves (SUMs / iButtons), not self-reported use. Many legacy cookstove credits have been criticised for over-crediting via inflated usage rates and emission factors.
- **Methane — livestock anaerobic digesters and landfill gas** — Generally robust on quantification; check additionality vs regulation (in jurisdictions where flaring is mandated, additionality fails) and whether subsidy-stacking changes the counterfactual.
- **Renewable energy** — In most geographies today, grid-connected renewables fail additionality. Most major registries have curtailed or excluded these. Treat any new RE-based VCM credit with strong skepticism.

## Co-benefits assessment

Carbon is one outcome; serious projects deliver more. Assess:
- **Biodiversity** — species monitoring, habitat connectivity, native-species share, third-party biodiversity certification (e.g., CCB Standards alongside VCS, Climate Community & Biodiversity Standards Gold-level).
- **Community livelihoods** — benefit-sharing agreement, what % of revenue goes to IPLCs, FPIC documentation, governance role for community.
- **Water** — hydrological monitoring, watershed-level outcomes.

For deeper biodiversity assessment, chain to `tnfd-leap`. For SDG-target-level impact mapping, chain to `impact-diligence`.

## Red flags — short list

If you see any of these, flag explicitly:
- Methodology version >5 years old without a transition plan
- Credits held unretired for >5 years marked-to-cost on a balance sheet (vintage decay risk)
- No independent third-party verification, or VVB used by the same project repeatedly with no rotation
- No community benefit-sharing agreement on a project located on / affecting IPLC lands
- Soil-carbon project claiming 100-year permanence with <10-year crediting period and no reversal mechanism
- REDD+ baseline set from a short reference period (<5 years) coinciding with anomalously high deforestation
- Cookstove project with self-reported usage rate >70% and no sensor data
- Cross-border corporate net-zero claim without a corresponding adjustment

## Public rating-agency cross-reference

Three carbon-credit rating agencies and one research nonprofit publish per-project assessments. Where the project being diligenced has a public rating, surface it:
- **Sylvera** — broadest coverage; ratings AAA through D
- **BeZero** — ratings AAA through D, methodology published
- **Renoster** — strong on forestry, more selective coverage
- **CarbonPlan** — independent nonprofit, deep-dive public analyses (especially on California IFM, US ARR, soil carbon, DAC)

Treat the rating as one input, not a verdict — read the underlying note. Where ratings disagree across agencies, the disagreement itself is informative.

## Output structure for memos

When producing the assessment, format as:

```
## Carbon Credit Quality Assessment — [Project / Fund / Offtake Name]

### Project Snapshot
- Project type: [ARR / IFM / REDD+ / ALM / Blue / DAC / Cookstoves / Methane / RE / Other]
- Methodology: [ID + version + registry]
- Vintage(s): [years]
- Volume: [tCO2e issued / projected]
- Geography: [country, sub-national if relevant]

### ICVCM CCP Scorecard
1. Effective governance: [pass / partial / fail / unknown] — [note]
2. Tracking: [pass / partial / fail / unknown] — [note]
3. Transparency: [pass / partial / fail / unknown] — [note]
4. Validation/verification: [pass / partial / fail / unknown] — [note]
5. Additionality: [pass / partial / fail / unknown] — [note]
6. Permanence: [pass / partial / fail / unknown] — [note]
7. Robust quantification: [pass / partial / fail / unknown] — [note]
8. No double counting: [pass / partial / fail / unknown] — [note]
9. Sustainable development & safeguards: [pass / partial / fail / unknown] — [note]
10. Net-zero transition contribution: [pass / partial / fail / unknown] — [note]

### Methodology Flags
- [Specific weakness of the methodology used]
- [Version-currency note]

### Registry Flags
- [Registry-specific governance / track-record notes]

### Five Quality Questions
- Additionality: [answer]
- Permanence: [answer + buffer % + reversal mechanism]
- Leakage: [answer + discount applied]
- Double counting: [answer + CA status if cross-border]
- MRV: [measurement / reporting / verification approach]

### Project-Type-Specific Concerns
- [Calibrated to the project type — see body of skill]

### Co-Benefits
- Biodiversity: [evidence]
- Community: [benefit-sharing, FPIC]
- Water / other: [evidence]

### Rating-Agency Cross-Reference
- [Sylvera / BeZero / Renoster / CarbonPlan — rating + key takeaway, if available]

### Bottom Line
- Disposition: [High quality / Moderate / Low / Reject]
- Top 3 reasons: [specific]
- Memo language recommendation: [precise phrasing for IC]
```

## When NOT to use this skill

- For general impact diligence — use `impact-diligence` first; chain here only if carbon credits are central.
- For biodiversity / nature-related risk that is broader than carbon — use `tnfd-leap`.
- For soil-carbon claims embedded in a regen-ag thesis where the credit issuance is secondary — start with `regen-glossary` to disambiguate the underlying practice, then return here for the credit assessment.
- For compliance-market carbon (EU ETS, CCA, RGGI) — different framework; this skill is voluntary-market focused.

## References

The supporting `assets/` folder contains:
- `methodology-flags.md` — known concerns per methodology ID
- `registry-comparison.md` — Verra / Gold Standard / ART / ACR / CAR / Plan Vivo comparison

If those files aren't present, the skill still works from the body above but with reduced specificity on methodology IDs and registry track-records.
