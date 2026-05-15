# fof-impact-nature-skills

Eight custom Claude Skills for fund-of-funds, impact, and natural-capital diligence — plus four Anthropic-published plugin bundles for financial-analysis, investment-banking, private-equity, and fund-admin (mirrored under `anthropic-plugins/` for convenience, Apache 2.0).

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

## Anthropic plugin ZIPs (`anthropic-plugins/`)

Four pre-zipped plugin bundles mirrored from [anthropics/financial-services-plugins](https://github.com/anthropics/financial-services-plugins) (Apache 2.0). Each archive contains the plugin's `.claude-plugin/plugin.json`, `commands/`, `hooks/`, and nested `skills/`.

| File | Inner skills |
|---|---|
| `financial-analysis.zip` | 3-statement-model, dcf-model, lbo-model, comps-analysis, competitive-analysis, audit-xls, clean-data-xls, deck-refresh, ib-check-deck, ppt-template-creator, pptx-author, xlsx-author, skill-creator |
| `investment-banking.zip` | buyer-list, cim-builder, datapack-builder, deal-tracker, merger-model, pitch-deck, process-letter, strip-profile, teaser |
| `private-equity.zip` | ai-readiness, dd-checklist, dd-meeting-prep, deal-screening, deal-sourcing, ic-memo, portfolio-monitoring, returns-analysis, unit-economics, value-creation-plan |
| `fund-admin.zip` | accrual-schedule, break-trace, gl-recon, nav-tieout, roll-forward, variance-commentary |

**Note on format:** these are Claude Code *plugin* bundles, not single SKILL.md skills. The intended install path is Claude Desktop → **Cowork tab** → Customize → Browse plugins → "Add marketplace from GitHub" → `https://github.com/anthropics/financial-services-plugins`. Drag-and-drop into the Settings → Skills uploader may not work since there's no top-level `SKILL.md`. If it doesn't, use the Cowork marketplace flow or Claude Code's CLI (`claude /plugin marketplace add anthropics/financial-services-plugins`).

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
