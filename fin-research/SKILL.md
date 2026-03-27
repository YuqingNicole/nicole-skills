---
name: fin-research
description: |
  Investment and financial research: stock analysis, crypto, earnings, valuations,
  portfolio health checks, sector scans. Outputs Markdown for quick queries,
  structured reports for deep analysis.

  USE WHEN:
  - "分析一下 XX 公司" / "research XX stock" / "XX 财报分析"
  - "BTC 现在怎么样" / "crypto market overview"
  - "帮我看看这个仓位" / "portfolio health check"
  - "XX 和 YY 怎么比" / "compare these two stocks"
  - "帮我找一些值得关注的标的" / "stock screening"
  - "XX 估值合理吗" / "is XX overvalued"
  - Earnings preview or post-earnings analysis

  DON'T USE WHEN:
  - General market research for a business idea → use research-engine skill
  - User asks "should I buy X" as casual chat → answer directly with caveats
  - Basic price lookup (single number) → web_search directly

  EDGE CASES:
  - "分析 XX 市场" for investing → this skill
  - "分析 XX 市场" for entering as a business → research-engine skill
---

# Financial Research

Investment-grade analysis for stocks and crypto. Quick queries in Markdown; deep research as structured reports.

---

## Output Format Decision

| Request type | Output |
|-------------|--------|
| Single data point ("BTC price", "AAPL P/E") | Inline Markdown, instant |
| Health check / morning brief | Markdown, structured sections |
| Deep analysis / initiating coverage | Full report (Markdown or HTML) |
| Comparison of 2+ entities | Side-by-side table + narrative |
| Earnings analysis | Structured report with beat/miss, guidance, thesis check |

---

## Scenario 1: Quick Query

Direct answer. Use web_search for live prices, ratios, recent news. Format:

- Single ticker: `**AAPL** $185.20 (+1.2%) | P/E 28.4 | Mkt Cap $2.84T`
- Multiple tickers: table with columns: Ticker | Price | Change% | Key Metric
- Crypto: price + 24h change + dominance if relevant

---

## Scenario 2: Portfolio Health Check

Systematic check across positions. Structure:

```
## Portfolio Snapshot [date]

### Position Health
| Ticker | Entry | Current | P&L% | Signal |
|--------|-------|---------|------|--------|

### Risk Flags
- [Any position with drawdown >15%]
- [Concentration >20% in single name]

### Upcoming Catalysts
- [Earnings dates, macro events in next 30 days]
```

---

## Scenario 3: Deep Research

For "research XX" / "cover XX" / "full analysis":

**Structure:**
1. **Thesis** — 2-3 sentences: what you believe, why, what would change your mind
2. **Business** — What they do, moat, key metrics
3. **Financials** — Revenue trend, margins, FCF, balance sheet
4. **Valuation** — Current multiples vs. historical vs. peers; DCF if relevant
5. **Catalysts** — What could move the stock in next 3-12 months
6. **Risks** — Top 3, with probability/impact assessment
7. **Pre-mortem** — "If this is down 30% in 6 months, what happened?"
8. **Verdict** — Buy / Hold / Avoid with conviction level

**Evidence tagging** (apply to all key claims):
- `[T1]` Primary: official filings, company data, verified earnings
- `[T2]` Factual: reputable press, research reports, verified metrics
- `[T3]` Inference: analyst opinion, forum discussion, AI synthesis

Rule: Thesis must rest on T1/T2. Pure T3 = opinion, not recommendation.

---

## Scenario 4: Earnings Analysis

Post-earnings or preview:

**Preview:** Consensus estimates + whisper number + key questions to watch  
**Post-earnings:**
1. Beat/miss on revenue, EPS, key metrics vs. consensus
2. Guidance: raised / maintained / lowered — magnitude matters
3. Management commentary: what changed in the narrative?
4. Thesis check: does this strengthen or weaken the original thesis?
5. Reaction assessment: is the stock move appropriate or overreaction?

---

## Scenario 5: Sector Scan

Find the strongest name in a sector:

1. Define the sector and key metrics that matter (margins, growth rate, FCF yield)
2. Pull top 5-8 names by market cap
3. Score each on: growth momentum, valuation, balance sheet, narrative
4. Rank and identify the best risk/reward

---

## Anti-Bias Checklist (Run Before Any Recommendation)

- [ ] Searched for the bear case, not just the bull case
- [ ] TAM/growth estimate cross-checked with at least 2 sources
- [ ] Compared to historical base rates for similar companies
- [ ] Pre-mortem completed: top 3 failure modes named explicitly
- [ ] All key claims labeled T1/T2/T3
- [ ] Checked: am I anchored to the first price/multiple I saw?

---

## Disclaimer

This is research, not financial advice. Nicole makes her own investment decisions.
All analysis is informational; past performance ≠ future results.
