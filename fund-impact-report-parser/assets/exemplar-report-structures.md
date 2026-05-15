# Exemplar fund impact report structures

A high-level structural map of how major impact-fund managers typically organize their annual impact reports. Use this to know *where* to look for each of the ten parser fields. This document describes structure only — it contains no verbatim content, metrics, or quotes from any actual report.

## General archetypes

Most institutional fund impact reports fall into one of three archetypes:

### Archetype A — narrative-led (typical of brand-forward managers)
- Letter from the CEO / managing partner
- "Our impact thesis" essay
- Portfolio highlight stories (case studies, 1–3 pages each)
- Headline metrics dashboard (often near the end)
- Methodology appendix (often thin)

**Where signal lives:** the methodology appendix and the case-study captions (which sometimes name third-party verifiers). The narrative essay is usually low signal for parsing — high on theory of change language, low on specifics.

**Watch for:** verification gaps. Narrative-led reports tend to assert outcomes that are actually outputs. The parser should flag every claim that has no methodology citation.

### Archetype B — framework-led (typical of institutional / IMP-aligned managers)
- IMP five-dimensions or similar framework as an organizing structure
- Per-portfolio-company impact pages keyed to the framework
- Explicit IRIS+ metric tables, often with metric IDs
- Third-party assurance statement (BlueMark, Tideline, KPMG, PwC, etc.) at the front or back
- Limitations and methodology section, usually substantive

**Where signal lives:** the per-company pages and the assurance statement. The metric tables are gold for IRIS+ extraction.

**Watch for:** IRIS+ codes cited in the methodology but not actually reported on. Also: framework-led managers sometimes substitute IMP language for IMP substance — e.g., naming "Contribution" as a dimension but providing no counterfactual.

### Archetype C — outcomes-led (typical of natural-capital, regen, or development-finance managers)
- Theory of change diagram, often early in the report
- Outcome-level metrics with baselines and measurement protocols
- MRV section describing on-site sampling, remote sensing, modeling
- Verifier / standard named (Verra, Gold Standard, Plan Vivo, EOV, ROC, etc.)
- Often includes peer-reviewed citations or links

**Where signal lives:** the ToC diagram (parse it directly) and the MRV section. These reports tend to be the most parser-friendly.

**Watch for:** carbon credit double-counting between "verified credits issued" and "estimated carbon impact." Also: regen vocabulary precision — apply `regen-glossary`.

## Typical sections to locate, in approximate order

When opening any report, scan the table of contents and locate as many of these as exist:

1. **Cover / front matter** — vintage year, AUM, portfolio company count, geography mix
2. **Letter from leadership** — usually skim only; rarely parser-relevant
3. **Impact thesis / theory of change** — primary source for Field 1
4. **Framework adopted** — IMP, IRIS+, SDG, OPIM (Operating Principles for Impact Management), HIPSO, or proprietary
5. **Portfolio dashboard** — headline numbers; usually output-level, not outcome-level
6. **Per-investment impact pages** — primary source for sector-specific extraction (regen, climate, livelihoods, health, etc.)
7. **Methodology / approach to measurement** — primary source for Fields 4 (verification) and 10 (gaps)
8. **Third-party assurance statement** — primary source for Field 4
9. **Limitations / caveats** — primary source for Field 7 (negative impact disclosure) and Field 10
10. **Appendices** — IRIS+ tables, SDG mapping tables, methodology details, glossary

## Sector-specific cues for Field 8 (regen / natural capital)

For managers with land-based or natural-capital theses, look additionally for:

- **Soil section** — SOC measurement depth (typically 0–30cm or 0–100cm), sampling methodology (composite vs paired, baseline year), modeling vs measurement
- **Biodiversity section** — species lists, habitat hectares, structural diversity indices, eDNA sampling, Bioacoustic monitoring
- **Water section** — infiltration tests, riparian buffer hectares, watershed-scale claims (almost always weaker than farm-scale)
- **Livelihoods section** — smallholder income data, ideally with baseline + comparison group; disaggregation by gender, age, geography
- **Land tenure section** — community land rights, FPIC processes — often absent and important
- **Certification mentions** — ROC, Demeter, Land to Market (EOV), Rainforest Alliance, Fair Trade, Bird Friendly, Plan Vivo
- **Carbon section** — separate verified registry credits from modeled carbon estimates; capture methodology IDs (VM0042, VM0017, VCS, AR-AMS0007, etc.)

## Sector-specific cues for Field 9 (carbon claims)

Locate any of:

- **Verified credits** — registry name, methodology ID, vintage, tCO2e, retired vs held, jurisdictional vs project-level
- **Avoided emissions** — counterfactual baseline approach, often the weakest link
- **Modeled emissions reduction** — model used (Cool Farm Tool, COMET-Farm, internal model), assumptions
- **Scope coverage** — Scope 1 / 2 / 3, attributional vs consequential, financed emissions methodology (PCAF)
- **Net zero or 1.5°C alignment claims** — SBTi status, interim targets, transition plan

## What to ignore

- Glossy infographics with no underlying data citation
- Stock-photo case-study captions without portfolio-company attribution
- Awards and accolades sections
- "Our team" pages
- Quotes from portfolio company founders without surrounding methodology

## Practical workflow

1. Skim the table of contents and tag each section against the parser's ten fields.
2. Read the methodology appendix and assurance statement *first* — this calibrates how to read the rest.
3. Read the ToC / impact-thesis section second — fills Field 1.
4. Pull IRIS+ IDs from the appendix or tables — fills Field 2.
5. Read per-investment pages selectively, looking for what was *measured* vs what was *asserted*.
6. Read the limitations section — fills Field 7 and informs Field 10.
7. Assemble the row from the template in SKILL.md.

If the report has none of these sections, the row should reflect that: ToC absent, IMP coverage absent, verification level 1, gaps pervasive. That is a legitimate parser output and a useful signal to the LP.
