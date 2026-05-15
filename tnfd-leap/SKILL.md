---
name: tnfd-leap
description: Use when assessing nature-related dependencies, impacts, risks, and opportunities for a fund manager, direct deal, portfolio company, or fund-of-funds book — especially in natural capital, real assets, agri/food, materials, real estate, infrastructure, or biotech. Applies the TNFD LEAP approach (Locate / Evaluate / Assess / Prepare) per the September 2023 v1.0 recommendations, integrates ENCORE dependency screening and SBTN target setting, and outputs a LEAP narrative plus TNFD disclosure scaffolding (C1–C8, S1–S6, RM1–RM3, M1–M8) usable for IC memos, LP reporting, and CSRD ESRS E4 alignment.
---

# TNFD LEAP — nature-related risk & opportunity diligence

## When to use this skill

Trigger this skill when any of the following appear:
- A deal, fund, or portfolio company has material interface with nature (land use, water, marine, forests, soils, biodiversity, ecosystem services)
- The user is preparing TNFD-aligned disclosure or CSRD ESRS E4 narrative
- A fund manager claims a "nature-positive" or "biodiversity" thesis and you need to test it
- The user asks "what's our nature exposure?", "is this in a sensitive ecosystem?", or "how should we report on biodiversity?"
- An LP investment committee is screening exposure across a fund-of-funds for nature-related systemic risk

Use this *alongside* `impact-diligence` — TNFD is about risk & disclosure; IMP/IRIS+ is about intentional impact. Both are usually needed for natural-capital deals.

## What this skill produces

A four-phase LEAP assessment plus TNFD-aligned disclosure scaffolding:

1. **LOCATE** — where the interface with nature sits (assets, value chain, sensitive ecosystems)
2. **EVALUATE** — what dependencies and impacts exist, screened via ENCORE-style sector logic
3. **ASSESS** — physical, transition, and systemic risks; opportunities
4. **PREPARE** — governance, strategy, risk management, metrics & targets, disclosure language
5. **Disclosure scaffolding** — populated stubs against the TNFD recommended disclosures

## The TNFD framing in one paragraph

TNFD (Taskforce on Nature-related Financial Disclosures) finalised v1.0 in September 2023. It mirrors the TCFD four-pillar structure — Governance / Strategy / Risk & Impact Management / Metrics & Targets — but for nature, defined as the four realms (land, ocean, freshwater, atmosphere). It is voluntary globally, but its disclosure architecture is being absorbed into mandatory regimes — most notably the EU CSRD's ESRS E4 (biodiversity & ecosystems), which is mandatory for in-scope entities. LEAP is the recommended *integrated assessment approach* feeding the disclosures.

## LEAP — the four phases

### LOCATE — interface with nature

Goal: identify where the organisation (or portfolio company, or fund's underlying assets) touches nature, and which of those touchpoints sit in sensitive areas.

Steps:
1. **Span of business model and value chain.** Direct operations, upstream (sourcing), downstream (sold products / financed activities). For a fund: aggregate to GP and underlying portfolio companies.
2. **Dependency and impact screening at sector level.** Use TNFD's priority sectors list (see `assets/priority-sectors.md`) — if the deal is in one of the 14 priority sectors, deeper LEAP is warranted by default.
3. **Interface with nature.** For each material activity / asset, identify:
   - Biome (per TNFD's biome typology — e.g., tropical/subtropical forests, temperate grasslands, freshwater wetlands, marine shelf)
   - Ecosystem services relied upon
   - Geographic footprint (site coordinates where possible)
4. **Interface with sensitive locations.** Overlay sites against:
   - Protected areas (WDPA — World Database on Protected Areas)
   - Key Biodiversity Areas (KBA)
   - Ramsar wetlands
   - IUCN Red List species ranges
   - High water-stress basins (WRI Aqueduct)
   - High deforestation-risk biomes (Global Forest Watch)
   - Indigenous & community lands

Practical tools (free / public): IBAT (Integrated Biodiversity Assessment Tool — free for non-commercial / capped use), WRI Aqueduct, Global Forest Watch, WWF Biodiversity Risk Filter, WWF Water Risk Filter, UNEP-WCMC Ocean+ Data Platform. See `assets/data-sources.md`.

Output of LOCATE: a list of sites/activities flagged "priority" for the deeper LEAP phases, with biome and sensitivity context.

### EVALUATE — dependencies and impacts

Goal: for the priority sites/activities, characterise the *dependencies* on nature and *impacts* on nature.

**Dependencies** — what ecosystem services the business relies on, e.g.:
- Provisioning: water supply, raw materials, genetic resources
- Regulating: pollination, climate regulation, flood/storm protection, water purification, disease control, soil quality regulation
- Cultural: recreation, spiritual values (rarely material to investors, but relevant for licence-to-operate)

Use ENCORE (Exploring Natural Capital Opportunities, Risks & Exposure) sector-by-dependency logic as a starting screen. ENCORE rates each sub-industry's materiality of dependence on each ecosystem service (Very Low → Very High). See `assets/encore-dependencies-quickref.md` for a high-level matrix and how to use the live ENCORE tool.

**Impacts** — the five direct drivers of nature change (per IPBES, adopted by TNFD):
1. Land/freshwater/sea use change (deforestation, conversion, drainage)
2. Direct exploitation (overharvest of timber, fish, water abstraction)
3. Climate change (the company's own GHG footprint as it drives nature loss)
4. Pollution (nutrients, pesticides, plastics, noise, light, chemicals)
5. Invasive alien species

For each, identify:
- The driver (which of the five)
- The pressure (e.g., hectares converted, m³ water withdrawn, kg N applied, tCO2e)
- The state change (loss of habitat, species decline, water table drop) — often only modellable, not directly measured
- Whether the impact is in a sensitive location identified in LOCATE

Quantify where data permits. Where it doesn't, say so explicitly — TNFD accepts qualitative narrative supported by sector-level proxies in early disclosure cycles.

### ASSESS — risks and opportunities

Goal: translate dependencies and impacts into financial risks and opportunities for the business and its investors.

**Physical risks** — from nature loss disrupting the business:
- Acute: a one-off event (wildfire destroys timber, fishery collapse, pollinator failure in a season)
- Chronic: gradual ecosystem service decline (soil degradation reducing yields, aquifer depletion, ocean acidification)

**Transition risks** — from society/markets responding to nature loss:
- Policy & legal: new permitting regimes, deforestation-free regulations (e.g., EUDR), nature-related litigation, biodiversity offsetting mandates
- Market: shifting buyer requirements (FMCG nature commitments cascading down supply chains), commodity price re-rating
- Reputation: campaigner / NGO targeting, social licence loss, indigenous rights conflicts
- Technology: substitution by lower-impact alternatives

**Systemic risks** — nature-related risks that propagate across the economy:
- Ecosystem collapse (e.g., Amazon dieback, coral reef collapse, pollinator collapse)
- Tipping points crossing thresholds beyond which recovery is implausible on policy-relevant timescales
- Financial system contagion via concentrated exposure to nature-dependent sectors (especially relevant at fund-of-funds level)

**Opportunities** — five TNFD categories:
1. Resource efficiency (water, materials, energy)
2. Products & services (nature-positive products, certified supply, restoration services)
3. Markets (new markets for biodiversity credits, restoration, blue economy)
4. Capital flow & financing (green/sustainability-linked debt, blended finance, nature-positive equity)
5. Resilience & reputation (durability of cash flows, licence to operate, talent retention)

For each risk and opportunity, characterise:
- Likelihood and magnitude (qualitative bands acceptable if no data — TNFD does not set numerical materiality thresholds)
- Time horizon (short / medium / long — define explicitly for the deal)
- Whether it affects revenue, cost, asset value, cost of capital, or strategic optionality

### PREPARE — to respond and report

Goal: convert findings into governance, strategy, risk management, metrics & targets, and disclosure language.

**Governance** — who owns nature at board / GP / portco level? Is it integrated with climate (TCFD), or siloed? TNFD recommends integrated climate-nature governance.

**Strategy adjustments** — what changes in business model, capital allocation, value-chain choices, or stewardship are warranted? For a fund: what changes in investment criteria, sourcing, engagement?

**Risk management** — how do nature risks flow into the firm's enterprise risk management? At LP/fund-of-funds level, how does nature exposure get aggregated across the book?

**Metrics & targets** — use TNFD's core global disclosure metrics (see below) plus, where appropriate, SBTN-aligned targets:
- SBTN provides the methodology for Science-Based Targets for Nature, covering Freshwater, Land, Biodiversity, and Ocean. Targets are set after a five-step process (Assess, Interpret & Prioritise, Measure-Set-Disclose, Act, Track) — the first two steps overlap heavily with LEAP-Locate and LEAP-Evaluate.
- TNFD provides the disclosure framework; SBTN provides the science-based target-setting methodology. They are complementary: many companies use LEAP to find their material interfaces, then SBTN to set defensible targets on them.

**Disclosure preparation** — produce narrative against TNFD's recommended disclosures, and check alignment with ESRS E4 (which is more prescriptive on scope, transition plan, materiality, and value-chain coverage).

## Integration with TCFD, CSRD ESRS E4, and SBTN

- **TCFD**: TNFD adopts the same four-pillar structure intentionally. The expectation is that filers produce integrated climate + nature disclosures, not two separate documents. Climate change is itself one of the five drivers of nature loss in the TNFD framework.
- **CSRD / ESRS E4**: Mandatory for in-scope EU and EU-listed companies under the CSRD. Requires double materiality (financial + impact materiality). TNFD/LEAP outputs feed E4 directly — but E4 has additional requirements (transition plan, policies, action plans, targets, value-chain coverage) that TNFD treats as recommended rather than mandatory. Treat TNFD as the diligence engine; ESRS E4 as the regulatory disclosure surface (where applicable).
- **SBTN**: Use SBTN methods when the user wants to set defensible science-based nature targets, not merely disclose. SBTN's Steps 1–2 (Assess / Interpret & Prioritise) are largely a re-skin of LEAP-Locate and LEAP-Evaluate; don't run them twice — reuse outputs.
- **GBF (Kunming-Montreal Global Biodiversity Framework)**: Provides the overarching policy goals (e.g., Target 15 on business disclosure, 30x30 on protected areas). Anchor the strategic narrative in GBF goals where the user is presenting to development-finance or policy audiences.

## TNFD core disclosure metrics — quick reference

TNFD's recommended disclosures are organised under the four pillars. Use these IDs as scaffolding in the output.

**Governance (C1–C8 in shorthand, formally Disclosures A–C):**
- Board oversight of nature-related dependencies, impacts, risks, opportunities
- Management's role
- Human rights policies and engagement with indigenous peoples, local communities, affected stakeholders

**Strategy (S1–S6, formally Disclosures A–E):**
- Material nature-related dependencies, impacts, risks, opportunities identified over short/medium/long term
- Effect on business model, value chain, strategy, financial planning
- Resilience of strategy under different scenarios
- Locations of assets/activities in priority areas (interface with sensitive locations)

**Risk and Impact Management (RM1–RM3, formally Disclosures A(i)–B):**
- Processes for identifying and assessing nature-related dependencies, impacts, risks, opportunities — in direct operations *and* upstream/downstream
- Processes for managing them
- Integration into overall enterprise risk management

**Metrics and Targets (M1–M8, formally Disclosures A–C):**
- Metrics used to assess material risks and opportunities
- Metrics used to assess dependencies and impacts (TNFD core global metrics — drivers of nature change, state-of-nature where measurable, response)
- Targets and performance against them

(Use the labels C1–C8, S1–S6, RM1–RM3, M1–M8 as working shorthand for memo structure. The formal TNFD lettering is alphabetical within each pillar — keep both available so the disclosure team can map cleanly.)

## The 14 priority sectors

TNFD's guidance identifies sectors where nature-related dependencies and impacts are systematically material and which therefore warrant deeper LEAP application by default. See `assets/priority-sectors.md` for the full list with rationale and typical LEAP focus areas. At a glance: food / agriculture / beverages, forestry & paper, mining & metals, oil & gas, chemicals, construction materials, utilities (water, electricity), real estate, infrastructure, transportation, biotech & pharma, apparel/textiles, consumer goods, and financials (as transmission belt).

If a deal is in one of these, expect: dependencies on water, soils, pollination, climate regulation, raw materials; impacts via land-use change, water abstraction, pollution, GHG; transition risk from EUDR / CSRD / sectoral regulation.

## Free public data sources

See `assets/data-sources.md` for the full list with access notes. Headline:
- **IBAT** — biodiversity site-screening (WDPA, KBA, IUCN Red List). Free for limited use; subscription for portfolio-scale.
- **Global Forest Watch** — tree cover loss, deforestation alerts, primary forest layers.
- **WRI Aqueduct** — water risk (baseline water stress, depletion, seasonal variability, flood, drought).
- **WWF Biodiversity Risk Filter** and **WWF Water Risk Filter** — site-and-portfolio-level risk screening.
- **UNEP-WCMC Ocean+ Data Platform** — marine and coastal data.
- **ENCORE** — sector dependency and impact ratings.
- **Trase** — commodity-driven deforestation traceability (soy, beef, palm, cocoa, coffee, others).

## Output structure for memos

When producing the TNFD LEAP assessment, format as:

```
## TNFD LEAP Assessment — [Fund / Deal / Company Name]

### LOCATE — interface with nature
- Business model span: [direct ops / upstream / downstream]
- Sectors (TNFD priority? Y/N): [list]
- Biomes touched: [list]
- Sites in sensitive locations: [WDPA / KBA / Ramsar / high water stress / high deforestation risk — with counts and sources]
- Priority assets/activities for deeper LEAP: [shortlist]

### EVALUATE — dependencies and impacts
- Material dependencies (ENCORE-screened): [list, with materiality rating]
- Material impacts by driver:
  - Land/sea use change: [pressure, magnitude, locations]
  - Direct exploitation: [...]
  - Climate change: [...]
  - Pollution: [...]
  - Invasive species: [...]
- Quantification status: [what's measured / modelled / qualitative-only]

### ASSESS — risks and opportunities
- Physical risks (acute, chronic): [list with horizon and financial channel]
- Transition risks (policy, legal, market, reputation, technology): [list]
- Systemic risks (tipping points, cascading exposure): [list]
- Opportunities: [list, mapped to the 5 TNFD opportunity categories]

### PREPARE — response and reporting
- Governance: [board/IC oversight, integration with climate]
- Strategy: [adjustments to investment criteria / portfolio / engagement]
- Risk management: [integration into ERM; aggregation across fund book]
- Metrics & targets: [TNFD core metrics applied; any SBTN targets contemplated]
- Disclosure positioning: [TNFD-aligned? ESRS E4-ready? gaps?]

### TNFD Disclosure Scaffolding
- Governance (C1–C8 / Disclosures A–C): [narrative stubs]
- Strategy (S1–S6 / Disclosures A–E): [narrative stubs, including priority locations]
- Risk & Impact Management (RM1–RM3 / Disclosures A(i)–B): [narrative stubs]
- Metrics & Targets (M1–M8 / Disclosures A–C): [metrics selected; targets if any]

### Bottom Line
- Nature-risk profile: [Material / Moderate / Limited] — with reasoning
- Top 3 things to push on in next conversation with GP / management: [specific]
- Memo language recommendation: [precise phrasing for IC, calibrated to evidence base]
```

## Caveats and what this skill does NOT do

- TNFD does **not** set numerical materiality thresholds. Don't invent ones (e.g., "X% biodiversity loss is material"). Use qualitative bands and name the evidence basis.
- TNFD is **voluntary**. Don't describe it as mandatory. ESRS E4 is mandatory for in-scope CSRD filers — be precise about which regime applies to the entity.
- Nature data is patchy. Many companies will not have site-level data. Say so. Use sector- and geography-level proxies and flag the uncertainty.
- This skill is **not** a carbon-credit or biodiversity-credit evaluator — for crediting integrity use a dedicated skill.
- This skill is **not** a substitute for legal counsel on disclosure obligations.

## When NOT to use this skill

- Pure climate-only diligence with no nature dimension → use TCFD-aligned climate skills.
- Pure impact-intentionality scoring → use `impact-diligence` (IMP/IRIS+).
- Regen-ag taxonomy disambiguation → use `regen-glossary` first, then return here for the nature-risk layer.
- Aggregating nature exposure across an LP fund-of-funds portfolio → use `fund-of-funds-diligence` for the portfolio-construction layer and chain to this skill per underlying fund.

## Chains to

- `impact-diligence` — for IMP five-dimensions and IRIS+ metric mapping where the deal also claims intentional positive impact
- `regen-glossary` — for precise vocabulary when LOCATE touches regenerative agriculture or land-use practices
- `fund-of-funds-diligence` — when aggregating nature exposure across underlying funds in an LP book

## References

The supporting `assets/` folder contains:
- `priority-sectors.md` — TNFD's 14 priority sectors with typical LEAP focus
- `encore-dependencies-quickref.md` — high-level sector-by-dependency matrix and how to use the live ENCORE tool
- `data-sources.md` — free public datasets for nature risk, with access notes

If those files aren't present, the skill still works from the body above but with reduced specificity.
