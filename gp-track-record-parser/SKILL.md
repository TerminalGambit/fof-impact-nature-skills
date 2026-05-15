---
name: gp-track-record-parser
description: Use when raw cash flow data (capital calls and distributions over time) for a GP's prior fund(s) is available and the LP needs to compute and interpret DPI, TVPI, RVPI, net IRR, MOIC, PME (Kaplan-Schoar and Direct Alpha), J-curve shape, loss ratio, return concentration, stale-mark signals, and vintage benchmark percentiles — typically as a deep-dive into the Track Record lens of `fund-of-funds-diligence`. Output is an evidence-graded track record memo with a re-up recommendation.
---

# GP track record parser — raw cash flow analytics for LP commitments

## When to use this skill

Trigger when any of the following hold:
- The LP has obtained deal-by-deal or fund-level cash flow schedules from a GP under NDA
- The GP-supplied summary stats need to be independently recomputed (Net IRR / MOIC / DPI / TVPI)
- A re-up decision is on the table and the prior fund needs a forensic read, not a marketing read
- Stale-mark or NAV-inflation risk is suspected (TVPI high, DPI flat, fund > 5 years old)
- Vintage benchmarking against Cambridge / Preqin / Burgiss / MSCI is needed and only summary stats have been provided
- A secondary purchase price needs to be triangulated against unrealized NAV credibility

**Use after `fund-of-funds-diligence`** when the Track Record lens (Lens 2) needs a deeper computational layer. The FoF skill identifies what to check; this skill does the check.

## Inputs expected

At minimum, one of:
1. Fund-level cash flow schedule: `(date, contribution, distribution, NAV)` per quarter
2. Deal-level cash flow schedule: `(deal, date, invested, realized, residual_value)`
3. Summary stats with a request to independently sanity-check

If only summary stats are provided, flag the limitation explicitly and produce a *bounded* read rather than a forensic one.

## Methodology — what to actually compute

### 1. The multiples — DPI, RVPI, TVPI

- **DPI = cumulative distributions / cumulative paid-in capital.** The only metric that survives audit. Post 7 years, DPI is the truth-teller.
- **RVPI = residual NAV / cumulative paid-in capital.** GP-marked. Treat with suspicion if RVPI dominates TVPI in a fund > 5 years old.
- **TVPI = DPI + RVPI.** Headline number. The DPI/RVPI *split* matters more than the total.

Interpretation rules:
- Fund age ≤ 4 yrs: TVPI dominated by RVPI is expected (J-curve). Focus on deployment pace and early write-up patterns.
- Fund age 5–7 yrs: DPI should be at least 0.3–0.5x in PE, 0.1–0.3x in VC. RVPI > 1.5x with DPI < 0.3x deserves a hard look.
- Fund age 8+ yrs: DPI should approach TVPI. Persistent RVPI of any size on an 8+ year fund is a stale-mark signal until proven otherwise.

### 2. Net IRR — and its sensitivity

Compute net IRR from the LP-perspective cash flow vector: contributions (-), distributions (+), and terminal NAV (+) on the as-of date. Use XIRR (Newton-Raphson on daily dates) — not annual approximations.

Always produce three IRR variants:
- **Reported Net IRR** — as the GP states it
- **Recomputed Net IRR** — from raw cash flows; should match within ~25 bps
- **DPI-only IRR** — terminal NAV set to zero. Difference between this and reported IRR = the IRR being carried by paper marks.

Sensitivities to run:
- Shift terminal NAV by ±20% — does the IRR collapse below the preferred return? If yes, the GP is one mark-down away from losing carry.
- Re-time the last 4 distributions by ±6 months — IRR moves materially if the fund engineered timing.
- Recompute on a "subsequent-close-adjusted" basis — early LPs subsidize late LPs' IRR; verify the schedule the GP used.

### 3. MOIC — gross vs net, always both

- **Gross MOIC** = total value at the deal level / invested at the deal level. Excludes fees, carry, fund expenses.
- **Net MOIC** = LP-level total value / LP-level paid-in. This is what shows up in your LP statement.

The gross-to-net spread should be ~0.4–0.7x for a mature PE/VC fund (20% carry, 2% mgmt fee, 10-year life). If the spread is < 0.3x, either the fund underperformed (no carry paid) or the fee math is non-standard — investigate. If the spread is > 0.8x, the fee load is unusually high.

### 4. PME — Kaplan-Schoar and Direct Alpha

A track record is meaningless without a public-market counterfactual. The illiquidity premium is the entire reason the asset class exists.

**Kaplan-Schoar PME (KS-PME):**
- Discount each LP cash flow by the total return of a public index from cash flow date to the as-of date.
- KS-PME = PV(distributions + terminal NAV) / PV(contributions).
- KS-PME > 1.0 means the fund outperformed the public index on a dollar-weighted basis.
- Read: KS-PME of 1.2 on a 10-year PE fund = 20% cumulative dollar outperformance vs the index. Modest.

**Direct Alpha:**
- IRR of cash flows discounted by the public index return.
- Direct Alpha = annualized excess return vs the public index.
- More intuitive than KS-PME for LP IC discussion. Target: 300+ bps for buyout, 500+ bps for VC, 200+ bps for infra.

**Benchmark selection** — pick the index that the strategy is genuinely an alternative to:
- US Large Buyout → S&P 500 Total Return
- US Mid/Small Buyout → Russell 2000 Total Return (or Russell 2500)
- US Venture → Russell 2000 Growth or Nasdaq Composite
- European PE → MSCI Europe
- Global Infrastructure → S&P Global Infrastructure Index or MSCI ACWI Infra
- Emerging Markets PE → MSCI EM
- Natural Capital / Timberland / Farmland → NCREIF Timberland / Farmland Index (closer to a comp than equities)
- Real Estate → NCREIF Property Index or NAREIT

If the GP cites a PME against the S&P 500 for a small-cap European buyout fund, that's marketing — recompute against MSCI Europe Small Cap.

### 5. J-curve shape analysis

Plot cumulative net cash flow (contributions negative, distributions positive) vs fund age in quarters. Compare to vintage-peer J-curve shape (Cambridge median).

Diagnostics:
- **Trough depth** — how negative does cumulative cash flow go? Deeper trough = slower fee/expense recovery.
- **Trough timing** — quarter at which cumulative cash flow bottoms. Median for PE buyout: Q14–Q18. Median for VC: Q18–Q24.
- **Break-even quarter** — when does cumulative cash flow cross zero? Faster than vintage median = real outperformance. Slower = drag.
- **Curve shape post-trough** — linear climb suggests steady realizations; step function suggests reliance on one or two big exits.

A fund that flattens at break-even (cumulative cash flow ~0) and stays there for 3+ years while RVPI stays high is the classic stale-mark profile.

### 6. Loss ratio — two definitions

- **Loss ratio (deal count)** = # deals returning < 1.0x / total # deals. Industry context:
  - Venture: 40–60% (power-law-driven)
  - Growth: 15–25%
  - Buyout: 5–15%
  - Infra / Real Assets: 5–10%
- **Loss ratio (capital weighted)** = capital in <1.0x deals / total invested capital. More informative than count — a fund can have a low count loss ratio but high capital loss ratio if the losers were large checks.

Compute both and report side by side. Red flag: capital-weighted loss ratio materially higher than count loss ratio = the GP wrote large checks into losers (selection or sizing problem).

A *too low* venture loss ratio (< 20% capital weighted in a 7+ year fund) is itself a flag — likely held-at-cost or written-up-to-last-round companies that haven't faced reality.

### 7. Concentration of returns

For each deal, compute: (realized + residual) - invested = absolute gain. Sort descending. Then compute:
- **Top-3-deal contribution to gross gain** = sum of top 3 deal gains / total fund gross gain
- **Fund TVPI excluding top 3** — what does the fund look like without the winners?
- **Loss coverage ratio** = gross gain from winners / gross loss from losers. < 2x means the winners barely cover the losers.

Industry context:
- Venture: top 3 deals routinely 60–90% of gain. This is normal. The question is whether the GP's process for *finding* these is repeatable.
- Buyout: top 3 deals typically 30–50% of gain. > 70% in buyout = concentration risk in disguise.
- Real assets: top 3 deals typically 20–40% of gain. Higher = portfolio construction failure.

If excluding the top 3 deals leaves the fund below 1.0x TVPI, the fund is a sourcing operation, not a portfolio-construction operation. That can be fine — but only if the sourcing edge is durable.

### 8. Stale-mark detection — six concrete tests

Run all six. Two or more flags = NAV inflation is a working hypothesis, not just a possibility.

1. **Mark-to-cost duration test** — any position held at cost > 5 years? Cost basis with no markup despite the rest of the fund maturing is either a write-down waiting to happen or active deferral.
2. **Last-round-only test** — positions marked only at the last priced round, with that round > 18 months stale, in a market that has materially repriced. Compare to public comp moves over the same window.
3. **Write-up cadence test** — does the GP write up positions in Q4 disproportionately (year-end optics)? Plot write-up events by quarter — Q4 clustering is a tell.
4. **Asymmetric markdown test** — write-ups happen quickly but write-downs lag. Compare time-to-write-up after a positive event vs time-to-write-down after a negative event.
5. **RVPI persistence test** — fund age > 6 years AND RVPI > 0.8x AND DPI < 1.5x = held value that the GP has not been able to realize. Could be patience, could be inability to exit.
6. **DPI/TVPI realization curve vs vintage peers** — plot DPI/TVPI ratio vs fund age. A fund persistently below the vintage median ratio is delaying realizations or carrying air.

### 9. Vintage benchmarking

Top-quartile in 2014 ≠ top-quartile in 2020. The vintage peer set must match: **strategy, geography, size band, and vintage year**.

Sources (cite explicitly in the memo, do not blend):
- **Cambridge Associates** — historically the LP standard; broad coverage
- **Preqin** — broadest manager coverage, weaker on cash flow detail
- **Burgiss / MSCI Private Capital** — generally considered the cleanest cash-flow-level dataset, used by many institutional LPs
- **Pitchbook** — strong on venture, weaker on buyout
- **eFront / StepStone** — increasingly used; consultant-driven

Report performance against benchmarks as percentile *bands*, not point estimates, because each provider's universe differs:
- Top quartile (top 25%)
- Second quartile (25–50%)
- Third quartile (50–75%)
- Bottom quartile (bottom 25%)

If three providers disagree on the quartile placement, say so — that disagreement is information.

A current top-quartile threshold reference table by strategy and vintage is in `assets/vintage-benchmarks-reference.md`. Refresh annually.

### 10. Re-up reasoning

Re-up is not a binary on prior fund performance. It's a forward-looking call informed by backward-looking data. The framework:

**Tier 1 — Track record gates** (must clear all three):
- Prior fund Net IRR ≥ vintage median (top half minimum)
- Prior fund DPI ≥ 0.5x if fund age ≥ 5 yrs, ≥ 1.0x if fund age ≥ 7 yrs
- PME / Direct Alpha positive vs appropriate benchmark

**Tier 2 — Process gates** (qualitative, but evidence-based):
- Concentration of returns is consistent with prior funds (no regime change in how the fund makes money)
- Loss ratio is in line with strategy norms — neither too high nor implausibly low
- Stale-mark signals from the six tests above are absent or explainable
- Team is intact (key partners who made the prior fund's winning calls are still investing)

**Tier 3 — Strategy gates** (overlaps with `fund-of-funds-diligence` Lens 3):
- Fund size step-up justified by deployment pace and market opportunity, not by AUM hunger
- Strategy is not drifting (sector, stage, geography consistent)
- Portfolio construction discipline visible in prior fund cash flows

**Default rule:** if Tier 1 fails, re-up is off the table absent extraordinary forward circumstances. If Tier 1 passes but Tier 2 has 2+ unresolved flags, recommend smaller-than-prior commitment with explicit conditions. Full re-up requires all three tiers clean.

## Output structure — track record memo section

When asked to parse a track record, produce:

```
## Track Record Analytics — [Fund Name] [Fund #] ([Vintage])

### Headline (recomputed, not as-reported)
| Metric | Value | vs. Reported | Notes |
|---|---|---|---|
| DPI | X.XXx | match / delta | |
| RVPI | X.XXx | | as-of date |
| TVPI | X.XXx | | |
| Net IRR | XX.X% | | recomputed XIRR |
| Net MOIC | X.XXx | | |
| Gross MOIC | X.XXx | | |

### Public Market Equivalent
| Benchmark | KS-PME | Direct Alpha | Interpretation |
|---|---|---|---|
| [index 1] | X.XX | +/-XXX bps | |
| [index 2 — sensitivity] | X.XX | +/-XXX bps | |

### J-Curve Diagnostics
- Trough quarter: Qxx (vs vintage median Qxx)
- Break-even quarter: Qxx (vs vintage median Qxx)
- Post-trough shape: [linear / step / flat]
- Read: [faster than peers / in line / slower]

### Loss & Concentration
- Loss ratio (deal count): X% (strategy norm: Y%)
- Loss ratio (capital weighted): X% (strategy norm: Y%)
- Loss coverage ratio: X.Xx
- Top-3-deal contribution to gross gain: X%
- Fund TVPI excluding top 3: X.XXx
- Concentration verdict: [sourcing-dependent / portfolio-built / mixed]

### Stale-Mark Tests (six tests)
1. Mark-to-cost > 5 yrs: [pass/fail — # positions, $ exposure]
2. Stale last-round marks: [pass/fail — # positions]
3. Q4 write-up clustering: [pass/fail]
4. Asymmetric markdown lag: [pass/fail — median days]
5. RVPI persistence: [pass/fail]
6. DPI/TVPI vs vintage curve: [pass/fail]
Overall NAV credibility: [Clean / Yellow / Red]

### Vintage Benchmark Placement
- Cambridge: [quartile, percentile if shown]
- Preqin: [quartile]
- Burgiss / MSCI: [quartile]
- Provider disagreement note: [if any]

### Re-Up Framework
- Tier 1 (Track Record Gates): [Pass / Fail — which]
- Tier 2 (Process Gates): [Pass / Fail — which flags]
- Tier 3 (Strategy Gates): [Pass / Fail — defer to FoF Lens 3]

### Recommendation
[Full re-up at $X / Reduced re-up at $Y with conditions / Pass / Defer pending data]
Top 3 questions for the GP before final decision:
1. ...
2. ...
3. ...
```

## Evidence grading — always state what you had to work with

End every memo with an evidence grade so the IC knows the confidence:
- **A** — fund-level + deal-level cash flows, audited statements, vintage peer data
- **B** — fund-level cash flows + summary deal stats
- **C** — summary statistics only (GP-provided); recomputation not possible
- **D** — pitchbook-only; treat as marketing read

Below grade B, do not state IRR / PME numbers to two decimal places — state them as bands, and flag the limitation.

## When NOT to use this skill

- For full GP commitment recommendation — use `fund-of-funds-diligence` and chain this skill into the Track Record lens
- For impact assessment — use `impact-diligence`
- For natural capital / regen-specific vocabulary disambiguation — use `regen-glossary` first
- For DCF / LBO of a single underlying portfolio company (co-invest underwriting) — use `financial-analysis:dcf` or `financial-analysis:lbo`
- For purely qualitative review without cash flow data — use `fund-of-funds-diligence` alone; this skill needs numbers

## Chaining with other skills

- **`fund-of-funds-diligence`** — primary parent. This skill is the deep-dive sub-skill for Lens 2 (Track Record). Run FoF first to scope the diligence, then this for the numerical layer, then return to FoF for the memo synthesis.
- **`impact-diligence`** — orthogonal. Track record analytics do not address impact quality. Run both for impact-aligned mandates.
- **`regen-glossary`** — use BEFORE this skill if the GP is a natural capital / regen ag / agroforestry fund and the deal sheet uses ambiguous vocabulary (e.g., "hectares under regenerative management").
- **`financial-analysis:dcf`, `:lbo`** — for stress-testing a specific portfolio company exit assumption that materially drives RVPI.
- **`investment-banking:comps`** — for triangulating exit multiple assumptions embedded in the RVPI.

## Supporting assets

The `assets/` folder contains:
- `vintage-benchmarks-reference.md` — top-quartile and median thresholds by strategy and vintage (refresh annually; sources cited)
- `pme-methodology.md` — KS-PME and Direct Alpha step-by-step worked methodology with edge cases (negative cash flows, mid-quarter close, currency)

If those files aren't loaded, this SKILL.md body is self-sufficient at lower precision — the user should be told that benchmark thresholds are approximate and that PME methodology should be verified against the reference before publishing the memo.
