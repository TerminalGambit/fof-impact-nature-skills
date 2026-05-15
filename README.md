# fof-impact-nature-skills

Eight custom Claude Skills for fund-of-funds, impact, and natural-capital diligence — plus 38 individual skill ZIPs extracted from Anthropic's financial-services plugins (financial-analysis, investment-banking, private-equity, fund-admin — Apache 2.0). Every ZIP is drag-drop-ready for Claude Desktop's Skills uploader (SKILL.md at the root of each archive).

Built for LP allocators, family offices, and impact-mandate investment teams. Each skill is self-contained — install whichever fit your workflow.

## The skills

| Skill | When to use |
|---|---|
| **`fund-of-funds-diligence`** | Sizing up a new GP for an LP commitment, secondary, or co-invest. Runs five analytical lenses (GP quality, track record, strategy, terms, portfolio fit). |
| **`gp-track-record-parser`** | Cash-flow deep dive — DPI / TVPI / RVPI / net IRR / MOIC / PME (Kaplan-Schoar + Direct Alpha) / J-curve / loss ratio / stale-mark detection. |
| **`lpa-redline`** | LPA review — produces clause-by-clause LP-favorable rewrites with negotiation rationale and ILPA / market precedent. |
| **`impact-diligence`** | IMP five-dimensions, IRIS+ metric mapping, SDG-target alignment, additionality stress-test. |
| **`fund-impact-report-parser`** | Comparable structured row per fund extracted from annual impact reports — for side-by-side IC packets. |
| **`tnfd-leap`** | Nature-related diligence — TNFD Locate / Evaluate / Assess / Prepare, ENCORE dependency screening, SBTN target setting, CSRD ESRS E4 alignment. |
| **`carbon-credit-quality`** | VCM credit assessment — ICVCM Core Carbon Principles, five quality questions (additionality, permanence, leakage, double counting, MRV), registry red flags. |
| **`regen-glossary`** | Vocabulary precision when "regenerative" / "agroecology" / "permaculture" / "biodynamic" are in play — disambiguates commonly-conflated terms. |

These chain. A regen-ag fund commitment, end-to-end:
`fund-of-funds-diligence` → `gp-track-record-parser` → `lpa-redline` → `impact-diligence` → `tnfd-leap` → `regen-glossary` → memo draft.

## Anthropic skill ZIPs (38 individual skills, at repo root)

Extracted from [anthropics/financial-services-plugins](https://github.com/anthropics/financial-services-plugins) (Apache 2.0). Each ZIP is a stand-alone Claude Desktop skill — `<skill-name>/SKILL.md` at the root of the archive, plus the Apache 2.0 LICENSE for attribution.

### From `financial-analysis` (13)
`3-statement-model.zip` · `audit-xls.zip` · `clean-data-xls.zip` · `competitive-analysis.zip` · `comps-analysis.zip` · `dcf-model.zip` · `deck-refresh.zip` · `ib-check-deck.zip` · `lbo-model.zip` · `ppt-template-creator.zip` · `pptx-author.zip` · `skill-creator.zip` · `xlsx-author.zip`

### From `investment-banking` (9)
`buyer-list.zip` · `cim-builder.zip` · `datapack-builder.zip` · `deal-tracker.zip` · `merger-model.zip` · `pitch-deck.zip` · `process-letter.zip` · `strip-profile.zip` · `teaser.zip`

### From `private-equity` (10)
`ai-readiness.zip` · `dd-checklist.zip` · `dd-meeting-prep.zip` · `deal-screening.zip` · `deal-sourcing.zip` · `ic-memo.zip` · `portfolio-monitoring.zip` · `returns-analysis.zip` · `unit-economics.zip` · `value-creation-plan.zip`

### From `fund-admin` (6)
`accrual-schedule.zip` · `break-trace.zip` · `gl-recon.zip` · `nav-tieout.zip` · `roll-forward.zip` · `variance-commentary.zip`

**Note:** these are the *skills* extracted from each plugin, not the full plugin (which would also include slash commands and hooks). Drag-drop each ZIP into Claude Desktop → Settings → Customize → Skills → `+` → Upload. If you also want the slash commands and hooks bundled with each plugin, install the full plugin via Claude Code: `claude /plugin marketplace add anthropics/financial-services-plugins` then `claude /plugin install <plugin-name>`.

## Install

### Claude Desktop (via Skills uploader)

1. Clone or download this repo.
2. For each skill folder you want, zip it (the folder itself, with `SKILL.md` at the root of the ZIP):
   ```bash
   cd fof-impact-nature-skills
   for d in */; do
     zip -r "${d%/}.zip" "${d%/}"
   done
   ```
3. In Claude Desktop: **Settings → Customize → Skills → `+` → Upload a skill**.
4. Upload each ZIP.
5. Confirm **Settings → Capabilities → "Code execution and file creation"** is on.

### Claude Code (via skills directory)

```bash
git clone https://github.com/TerminalGambit/fof-impact-nature-skills.git
mkdir -p ~/.claude/skills
cp -R fof-impact-nature-skills/*/ ~/.claude/skills/
```

Each skill activates automatically when the conversation matches its `description:` frontmatter — no manual invocation needed. You can also invoke explicitly with `/<skill-name>`.

## Structure

Each skill is a directory with `SKILL.md` at the root (YAML frontmatter + body). Some include an `assets/` folder with reference data (e.g. `impact-diligence/assets/sdg-targets-reference.md`, `lpa-redline/assets/`).

```
fof-impact-nature-skills/
├── carbon-credit-quality/
│   └── SKILL.md
├── fund-impact-report-parser/
│   └── SKILL.md
├── fund-of-funds-diligence/
│   └── SKILL.md
├── gp-track-record-parser/
│   └── SKILL.md
├── impact-diligence/
│   ├── SKILL.md
│   └── assets/
├── lpa-redline/
│   ├── SKILL.md
│   └── assets/
├── regen-glossary/
│   └── SKILL.md
└── tnfd-leap/
    └── SKILL.md
```

## Frameworks referenced

- **IMP** — Impact Management Project five dimensions
- **IRIS+** — GIIN's metric catalog
- **ICVCM CCPs** — Core Carbon Principles
- **TNFD LEAP** — Taskforce on Nature-related Financial Disclosures v1.0 (Sept 2023)
- **ENCORE** — UNEP-FI / Global Canopy dependency screening
- **SBTN** — Science Based Targets for Nature
- **ILPA** — Institutional Limited Partners Association principles
- **CSRD ESRS E4** — EU sustainability reporting (biodiversity)
- **UN SDGs** — Sustainable Development Goals targets

## Compatibility

Skills follow the [Agent Skills open standard](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) — the same `SKILL.md` directory runs unchanged across Claude.ai, Claude Desktop, Claude Code, and the Claude API.
