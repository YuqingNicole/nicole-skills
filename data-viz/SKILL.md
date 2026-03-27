---
name: data-viz
description: |
  Create charts, tables, and Excel files from data. Covers Python (matplotlib/seaborn),
  xlsxwriter Excel reports, and quick in-chat table formatting.
  Provides Nicole's color palette, Chinese font config, and chart type decision logic.

  USE WHEN:
  - "画个图" / "做个图表" / "visualize this data"
  - "生成 Excel" / "导出表格" / "export to spreadsheet"
  - Analyzing Reddit karma trends, SEO metrics, product data, or any tabular data
  - "帮我看看这组数据" with numbers attached

  DON'T USE WHEN:
  - Single number or 2-row comparison → just say the number in text
  - User wants a business analysis report → use research-engine skill
  - User wants a presentation → use AnyGen (if available) or describe manually

  EDGE CASES:
  - Data has CJK characters in labels → check font config in references/matplotlib.md
  - User says "chart" but has only 2 data points → KPI card or text comparison is better
---

# Data Viz

Generate charts, tables, and Excel files. Match the output format to the data and the question.

---

## Decision: What to Build

Ask three questions before choosing:
1. **What is the reader comparing?** (magnitude, trend, proportion, correlation, stage drop-off)
2. **Do they need precise numbers?** If yes → add data labels or pair with a table
3. **How many categories/series?** More series = higher risk of unreadable chart

| Data type | Build |
|-----------|-------|
| Single number | Text / KPI callout — no chart |
| 2-row comparison | Text with bold numbers |
| Rankings / multi-entity list | Styled table (Template 1 in references/excel.md) |
| Trend over time | Line chart |
| Category comparison | Column (vertical) or Bar (horizontal, long labels) |
| Composition/share | Pie (≤5 slices) or stacked bar |
| Stage drop-off | Funnel |
| Correlation | Scatter |
| Multi-metric profile | Radar |
| Structured report | Excel with charts (Template 2 or 3 in references/excel.md) |

---

## Chart Type Rules

- **Pie**: max 5 slices. More → use sorted bar chart.
- **Funnel**: only when values decrease at each stage AND same unit throughout.
- **Line**: requires ≥5 time points to show meaningful trend.
- **Stacked**: only when the total has business meaning.
- **Combo (bar + line)**: exactly 2 metrics, x-axis must be temporal or ordered with ≥5 points.

---

## Output Paths

**In-chat chart (matplotlib PNG):**  
Save to `~/workspace/artifacts/charts/YYYY-MM-DD-[slug].png`  
See `references/matplotlib.md` for style constants and templates.

**Excel report:**  
Save to `~/workspace/artifacts/data/YYYY-MM-DD-[slug].xlsx`  
See `references/excel.md` for xlsxwriter templates.

---

## Style Constants

Nicole's palette (use consistently):

```python
COLORS = {
    'primary':   '#4A90A4',   # blue-gray — main series
    'accent':    '#E07B54',   # coral — highlight / second series
    'success':   '#6B9B7A',   # sage green — positive change
    'warning':   '#D4A84B',   # amber — caution
    'neutral':   '#8B9298',   # gray — background series
}

HEADER_BG   = '#0D1B3E'  # dark navy — Excel header background
SECTION_BG  = '#1E3A5F'  # mid navy — Excel section headers
POS_COLOR   = '#16A34A'  # green — positive delta
NEG_COLOR   = '#DC2626'  # red — negative delta
```

For full matplotlib setup, chart templates, CJK font config → `references/matplotlib.md`  
For Excel styling, xlsxwriter templates, chart placement → `references/excel.md`

---

## Anti-Patterns

- ❌ Charting raw data with 10k rows — aggregate first
- ❌ Rainbow color palettes — max 6 distinct colors
- ❌ 3D charts — always flat
- ❌ Dual Y-axes — use separate charts
- ❌ Labels so long they get truncated — shorten to ≤15 chars
- ❌ Percentage column formatted as 0–100 integer with `.1%` formatter (outputs "8500%")
- ❌ Unscaled large numbers on axes (6000000 → pre-scale to 6.0M)
