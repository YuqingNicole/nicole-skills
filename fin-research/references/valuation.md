# Valuation Reference

## Common Multiples

| Multiple | Formula | Best for | Red flags |
|----------|---------|---------|-----------|
| P/E | Price / EPS | Profitable companies, steady earnings | Negative earnings, cyclicals at peak |
| P/S | Price / Revenue | High-growth, pre-profit companies | Ignores margins |
| EV/EBITDA | Enterprise Value / EBITDA | Capital-intensive businesses | Ignores capex |
| P/FCF | Price / Free Cash Flow | Cash-generative businesses | Better than P/E for real economics |
| P/B | Price / Book Value | Banks, asset-heavy businesses | Meaningless for software |
| EV/Revenue | Enterprise Value / Revenue | SaaS, early-stage growth | Compare only within sector |

## DCF Quick Framework

Use when: company has predictable FCF, or for sanity-checking a valuation.

```
Intrinsic Value = Σ (FCF_year_n / (1 + r)^n) + Terminal Value / (1 + r)^N

Where:
- r = discount rate (typically 8–12% for equities)
- Terminal Value = FCF_N × (1 + g) / (r - g)
- g = terminal growth rate (typically 2–4%)
```

Sensitivity table: always show value at r ± 2% and g ± 1%.

## Relative Valuation

1. Find 3–5 comparable companies (same sector, similar growth profile)
2. Get their current multiples
3. Justify why the target deserves a premium or discount:
   - Premium: better growth, stronger moat, higher margins
   - Discount: execution risk, balance sheet, smaller scale

## Crypto Valuation

Different frameworks:
- **NVT Ratio** (Network Value to Transactions): Price × Supply / On-chain transaction volume. High NVT = overvalued relative to usage.
- **Stock-to-Flow**: Scarcity model for BTC. Controversial but widely referenced.
- **Relative to ETH/BTC**: What premium/discount does this token trade at vs. market cap of comparable assets?
- **Protocol Revenue**: For DeFi — EV/Revenue or Price/Fee multiple.

## Key Metrics by Sector

| Sector | Primary metric | Secondary |
|--------|---------------|-----------|
| SaaS | ARR growth, NRR, Rule of 40 | CAC payback, churn |
| E-commerce | GMV growth, take rate, margin | Customer LTV |
| Fintech | Revenue per user, credit quality | Regulatory exposure |
| Consumer | Same-store sales, unit economics | Brand NPS |
| Hardware | Gross margin, inventory turns | ASP trend |
| Crypto L1 | Developer activity, TVL, tx volume | Token inflation rate |
