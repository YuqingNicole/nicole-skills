---
name: research-engine
description: |
  Deep research and strategy analysis. Combines McKinsey 12-module framework with
  institutional-grade methodology: evidence grading, anti-bias checks, pre-mortem.
  
  USE WHEN:
  - "帮我分析市场" / "做竞品分析" (for strategy, not shopping)
  - "研究一下这个赛道" / "market research" / "industry analysis"
  - "做个商业分析" / "帮我做 GTM 策略"
  - Deep-dive on a company, product, or sector
  - Investment thesis or due diligence
  - "找竞品" / "分析用户" / "做定价研究"

  DON'T USE WHEN:
  - "推荐什么产品买" → answer directly
  - Simple web search for a company fact → web_search directly  
  - User wants a quick take on an idea → answer directly
  - "比较一下 A 和 B 哪个好买" → answer directly

  EDGE CASES:
  - "分析市场" with a product to purchase → answer directly
  - "分析市场" for business entry decision → USE this skill
  - "做竞品分析" about products to buy → answer directly
  - "做竞品分析" as startup strategy → USE this skill
---

# Research Engine

Deep research with structure. Combines the 12-module McKinsey framework with evidence grading and anti-bias methodology.

---

## When to Run Full 12-Module vs. Targeted

| Request | Mode |
|---------|------|
| "做个完整市场分析" / "full strategy report" | Full 12-module (see below) |
| "帮我分析竞争格局" | Module 2 only |
| "做用户画像" | Module 3 only |
| "估算一下 TAM" | Module 1 only |
| "帮我想定价策略" | Module 5 only |
| Quick company background | web_search + 3-paragraph summary |

---

## Full 12-Module Framework

Run modules in parallel via sub-agents. Synthesize into HTML report at end.

| # | Module | Output |
|---|--------|--------|
| 1 | TAM/SAM/SOM sizing | Market size estimate with confidence range |
| 2 | Competitive landscape | 3×3 matrix: players × dimensions |
| 3 | Customer persona | 2–3 archetype profiles |
| 4 | Problem-solution fit | Pain severity × solution uniqueness |
| 5 | Pricing strategy | Anchors, tiers, willingness-to-pay |
| 6 | Go-to-market | Channel strategy, sequencing, first 90 days |
| 7 | Financial model | Revenue scenarios, unit economics, break-even |
| 8 | Risk matrix | 5×5 grid: probability × impact |
| 9 | SWOT | With evidence citations |
| 10 | Market entry | Timing, beachhead, moat |
| 11 | China/Asia specifics | WeChat ecosystem, 私域, PIPL, 港台/东南亚 if relevant |
| 12 | Synthesis | Executive summary + 3 actionable recommendations |

Report saved to: `~/workspace/artifacts/research/YYYY-MM-DD-[slug].html`

---

## Evidence Framework (Apply to All Research)

Label every key claim:

| Tier | Definition | Example |
|------|-----------|---------|
| **T1** | Primary data: official filings, your own data, direct measurements | SEC filing revenue figure |
| **T2** | Factual secondary: verified news, academic papers, reputable market reports | Crunchbase funding round |
| **T3** | Opinion/inference: analyst commentary, forum discussion, AI synthesis | "Industry observers believe..." |

**Rule:** A thesis that rests only on T3 evidence cannot justify a strategic recommendation.

---

## Anti-Bias Checklist

Run before finalizing any recommendation:

- [ ] **Confirmation bias**: Did you search for evidence against the thesis?
- [ ] **Anchoring**: Is your TAM estimate anchored to the first number you found?
- [ ] **Availability bias**: Are you overweighting recent news vs. base rates?
- [ ] **Pre-mortem**: "If this strategy fails in 12 months, what are the 3 most likely causes?"

Pre-mortem is mandatory before any strategic recommendation. Write it out explicitly.

---

## Output Format

**Short analysis (targeted module):** Markdown in chat  
**Full 12-module:** HTML report

HTML report structure:
1. Executive summary (1 page)
2. Module sections (labeled T1/T2/T3 where relevant)
3. Pre-mortem section
4. 3 concrete recommendations with owner + timeline

---

## Intake Form (Full Research)

Collect once, then execute without re-asking:

```
【必填】
1. 产品/服务：
2. 行业/赛道：
3. 目标用户：
4. 地区：

【选填 — 提升精度】
5. 当前定价：
6. 阶段：[想法 / 初创 / 成长 / 成熟]
7. 最大挑战：
8. 12 个月目标：
```

Unfilled fields marked `[未提供]`, analysis proceeds regardless.
