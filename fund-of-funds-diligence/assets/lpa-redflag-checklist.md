# LPA Red-Flag Checklist

A checklist for spotting economic and governance terms that should be negotiated, push-back-on, or veto-trigger. Not a substitute for legal counsel — this is what to surface to legal.

## Economic terms

### Management fee
| Pattern | Verdict |
|---|---|
| 1.5-2.0% on committed during investment period, step-down to invested/NAV after | Standard |
| 2.0%+ on committed with no step-down | LP-unfavorable — push back |
| 2.5%+ on committed | Generally unacceptable except for emerging managers with strong attribution |
| Fee on aggregate vs net of distributions to partners | Always net of partner distributions |
| "Subsequent closer" fees retroactive to first close (interest charged) | Standard |
| No retroactive fee for late closers | LP-favorable for late closers, but ask about catch-up mechanics |

### Carry
| Pattern | Verdict |
|---|---|
| 20% European waterfall (whole-fund) | Standard, LP-favorable |
| 20% American waterfall (deal-by-deal) | Common in VC, but verify strong clawback |
| 25-30% carry | Justified only for top-quartile sustained VC; otherwise excessive |
| 100% catch-up to GP after hurdle | Standard but extractive; 80/20 catch-up better |
| GP catch-up of 80%+ | Push back |
| Clawback gross of taxes | LP-favorable |
| Clawback net of taxes | GP-favorable; push back |
| No interest on clawback | GP-favorable; standard ask is risk-free rate |

### Hurdle / preferred return
| Pattern | Verdict |
|---|---|
| 8% pref in PE/infra | Standard |
| No hurdle in VC | Standard for venture |
| No hurdle in PE | Push back |
| Compounded annually | Standard |
| Cumulative non-compounded | LP-unfavorable |

### GP commitment
| Pattern | Verdict |
|---|---|
| < 1% of fund | Weak alignment; major concern for emerging managers |
| 1-2% | Minimum standard |
| 2-5% | Strong alignment |
| 5%+ | Excellent alignment |
| Funded via management fee waiver | Weaker than out-of-pocket; verify |
| Borrowed against fund commitment | Effectively reduces alignment |

### Fund expenses
| Pattern | Verdict |
|---|---|
| Organizational expense cap (typically 0.5-1.0% of commitments or $1-2M) | Standard, should exist |
| Broken deal expenses borne by fund | Standard |
| Dead deal fees borne by fund | Standard but should be capped |
| Travel / entertainment in fund expenses | Push back — should be management company |
| Marketing / placement agent in fund expenses | Push back — should be management company |
| 100% offset of transaction fees against mgmt fee | Standard LP win — verify still applies |
| Partial offset (60-80%) | Push back — 100% is the standard now |

## Governance terms

### Key-person clause
| Pattern | Verdict |
|---|---|
| Named individuals trigger investment period suspension | Standard |
| Only one person named | Single point of failure — push back |
| Suspension auto-reactivated after 6 months | Push back — should require LP advisory committee approval |
| LPAC has full veto on replacement | LP-favorable |
| GP discretion to replace key person | Push back |

### Removal & no-fault divorce
| Pattern | Verdict |
|---|---|
| 75% LP supermajority can remove GP without cause | Standard |
| 80%+ required (or supermajority by capital, not headcount) | Push back |
| Removal with cause: 50% threshold | Standard |
| "Cause" narrowly defined | Push back — should include material breach, fraud, gross negligence |
| Removal carries termination penalty to GP | Push back |

### Reinvestment / recycling
| Pattern | Verdict |
|---|---|
| Recycling of distributions during investment period | Common in PE |
| Cap on recycling (typically 110-120% of commitments) | Standard |
| Uncapped recycling | Push back |
| Recycling outside investment period | Generally not permitted in well-structured LPAs |

### Reporting
| Pattern | Verdict |
|---|---|
| ILPA-compliant quarterly reports | Standard expectation |
| Audited annual financials within 90 days | Standard |
| Look-through to portfolio company financials | LP-favorable, common ask |
| Portfolio company KPI tracking | LP-favorable, push for if missing |
| For impact mandates: aligned impact reporting (IRIS+ / Operating Principles) | Verify |

### LPAC (LP Advisory Committee)
| Pattern | Verdict |
|---|---|
| LPAC with conflict-of-interest approval rights | Standard |
| LPAC seats allocated to top X LPs by commitment | Standard |
| LPAC has valuation review role | LP-favorable |
| LPAC purely advisory, no veto rights | Push back on conflicts |

### MFN (Most Favored Nation)
| Pattern | Verdict |
|---|---|
| Open MFN — all LPs see all side letters | LP-favorable |
| Tiered MFN by commitment size | Standard for large funds |
| MFN excludes LPs above certain commitment | Verify the threshold isn't above your commitment |
| Broad carve-outs (regulatory, ERISA, sovereign) | Standard, but verify carve-outs are genuinely necessary |
| Election deadline shorter than 30 days | Push back |

### Other terms to scrutinize
- **Indemnification of GP** — standard, but should be net of insurance recoveries
- **Defense costs** — should be advanced subject to repayment if found liable for misconduct
- **Conflict transactions** — affiliated transactions require LPAC approval
- **GP's other fund commitments** — exclusivity period during this fund's investment period
- **Fund extensions** — typically two one-year extensions; LP consent required
- **Successor fund** — GPs should not raise successor before X% of fund is invested

## Impact-specific LPA terms

For impact-aligned funds, additionally check:
- **Mission lock** — what protects the impact thesis from drift? Constitutional document, side letter, or governance?
- **Impact reporting standards** — IRIS+ / IMP / GIIN Operating Principles compliance referenced in LPA
- **Impact carry / fee tied to impact metrics** — increasingly common in newer funds
- **Negative screen carve-outs** — does the LPA prohibit specific investments (fossil fuels, weapons, etc.)?
- **Stakeholder governance** — community / worker / beneficiary representation in governance structures
- **Theory of change** — referenced in LPA recitals?

## How to use the output of this checklist

When this skill is invoked on an LPA, produce:

```
## LPA Red Flags — [Fund Name]

### Top 5 to negotiate (by impact on LP economics/governance)
1. [Term] — Current: X / Standard: Y / Recommendation: Z
2. ...

### Acceptable but worth noting
- ...

### Disqualifying terms
- [If any — these are commit-vetoes]
```

Always recommend the LP also routes the LPA through legal counsel — this skill identifies issues, doesn't replace legal review.
