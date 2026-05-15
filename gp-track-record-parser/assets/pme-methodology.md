# PME methodology — Kaplan-Schoar and Direct Alpha, step by step

This reference is for the parser to apply correctly and to defend the calculation under IC questioning. Two methods are covered. Use both; they answer different questions.

## Inputs required

For each LP cash flow `i`:
- `t_i` — cash flow date (use actual date, not period-end approximation)
- `CF_i` — signed cash flow (contributions negative, distributions positive)
- Plus: terminal NAV on as-of date `T`, treated as a positive cash flow at `T`

For the benchmark:
- `I_t` — total return index level on date `t` (price index alone is wrong — must include dividends reinvested)
- `I_T` — index level on as-of date `T`

## Kaplan-Schoar PME

### Concept

KS-PME asks: "If every dollar called had instead been invested in the public index, and every dollar distributed had been pulled out of the index on the same dates, how much money would we have at `T` vs what the fund actually delivered?"

### Formula

For each cash flow, define a discount factor:
```
DF_i = I_T / I_{t_i}
```

Future-value each cash flow to date `T` using the index growth from `t_i` to `T`:
```
FV_i = CF_i × (I_T / I_{t_i})
```

Then:
```
KS-PME = [Σ FV(distributions) + FV(terminal NAV)] / [Σ FV(contributions taken as positive)]
```

Equivalently in present-value form (discount everything back to `t = 0`):
```
KS-PME = PV(distributions + terminal NAV) / PV(contributions)
```

Both forms give the same ratio.

### Interpretation

- KS-PME = 1.0 → fund matched the index on a dollar-weighted basis
- KS-PME > 1.0 → fund outperformed; value is the multiple of outperformance on the dollars invested
- KS-PME < 1.0 → fund underperformed; the LP would have done better in the index

Common watermark: a KS-PME of 1.20 over a 10-year horizon is moderate outperformance; 1.40+ is strong. For VC funds vs Russell 2000 Growth, top-quartile funds historically land 1.3–1.6+.

### Pitfalls

- **Wrong index** — KS-PME of 1.5 vs S&P 500 for a European mid-market buyout fund is meaningless. Match the index to the strategy's actual investable alternative.
- **Price-only index** — using S&P 500 price return instead of total return understates the public market alternative by ~150–200 bps annually. Always use total return.
- **Currency mismatch** — fund reported in USD, index in local currency, or vice versa, will produce spurious alpha or drag. Either convert cash flows to a single currency before PME, or pick an index in the same currency.
- **Terminal NAV credibility** — KS-PME of a 6-year-old fund with TVPI dominated by RVPI is largely a statement about the GP's marks. Pair with the stale-mark tests in the main skill.

## Direct Alpha

### Concept

Direct Alpha converts the PME into an annualized excess return — the answer to "how many basis points per year did the fund beat the index?"

### Formula

1. Compute the index-discounted cash flows:
```
CF*_i = CF_i × (I_T / I_{t_i})    [same future-value transform as KS-PME]
```
2. Solve for the IRR of the index-discounted cash flow series (including terminal NAV).
3. That IRR is the Direct Alpha — the annualized rate of return *in excess of* the public index.

### Interpretation

- Direct Alpha = 0% → matched the index annualized
- Direct Alpha > 0% → outperformed by that many bps per year
- Direct Alpha < 0% → underperformed by that many bps per year

Institutional targets (rough):
- US Buyout: 300+ bps Direct Alpha vs S&P 500
- US VC: 500+ bps Direct Alpha vs Russell 2000 Growth or Nasdaq
- European PE: 300+ bps vs MSCI Europe
- Infrastructure: 200+ bps vs S&P Global Infrastructure
- Real estate value-add: 200–300+ bps vs NCREIF Property
- Natural capital: 100–200+ bps vs NCREIF Timberland/Farmland

### Why Direct Alpha is easier to discuss at IC

KS-PME of 1.18 over 9 years is harder to convey than "this fund returned ~180 bps per year above the public index." Both are correct; one is more useful in a memo.

## Edge cases and engineering details

### Negative cash flows after distributions

If the fund recycles (recalls distributed capital), the cash flow becomes negative again partway through. The PME math handles this naturally — just sign the flows correctly. But verify that the cash flow series you received reflects net recycling, not gross.

### Mid-quarter cash flows

Use actual transaction dates and daily index levels (or interpolate the index linearly between month-ends if only month-end data is available). Period-end approximations introduce noise that can move a PME of 1.05 vs 1.15 — material for quartile placement.

### Currency

If the fund is USD-denominated but invests in EUR/GBP/AUD assets, the GP's reported returns already bake in FX. Match the PME benchmark currency to the fund's reporting currency, not to the underlying assets, unless you specifically want an FX-stripped alpha.

### Subsequent-close adjustments

Funds with rolling closes generate equalization payments — late LPs pay catch-up interest to early LPs. The cash flow series should be from a consistent LP perspective. If you're using an early-LP series, the fund will look better than reality; if a late-LP series, worse. Verify which the GP provided.

### Stub period at the start

If the fund called its first contribution mid-quarter, do not push it to the prior quarter-end. PME is sensitive to early timing because contributions sit longest. Use actual dates.

### Sensitivity sweeps to run before publishing

1. Two indices (primary + secondary) — e.g., S&P 500 and Russell 2000 for a US growth fund. If PME flips sign across them, flag.
2. Two as-of dates — most recent quarter and one quarter prior. Big swing = NAV mark just moved.
3. Terminal NAV at ±20%. If Direct Alpha flips sign with -20% NAV, the alpha is paper alpha.

## Output template for the PME section of the memo

```
### Public Market Equivalent

| Benchmark | Universe match | KS-PME | Direct Alpha | Sensitivity |
|---|---|---|---|---|
| Primary: [Index] | [strong/partial] | X.XX | +/-XXX bps | NAV ±20% → [stable / flips] |
| Secondary: [Index] | [strong/partial] | X.XX | +/-XXX bps | |

Interpretation: [1–3 sentences. State the fund's annualized excess return vs the public alternative, whether that justifies the illiquidity, and how sensitive it is to NAV credibility.]
```

## When PME is not the right tool

- Funds < 4 years old — PME is noisy until enough cash flow has occurred
- Funds where the relevant public counterfactual genuinely does not exist (very early-stage frontier-market venture, novel ecosystem service plays). In those cases, use a NCREIF-style asset benchmark or skip PME and rely on Direct Alpha sensitivity bands.
- Funds where terminal NAV is > 60% of TVPI and the marks are uncorroborated — PME inherits the mark risk. State the bound.
