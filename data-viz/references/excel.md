# Excel (xlsxwriter) Reference

## Rules
- Use `xlsxwriter` only — never `pandas.to_excel()` (no styling)
- Header row: dark navy `#0D1B3E` bg, white bold text — non-negotiable
- Positive delta: `#16A34A` green. Negative: `#DC2626` red.
- Column widths: fit content. CJK chars count as 2. Minimum 10.
- One sheet preferred. Multiple sheets only if explicitly requested.
- Save to: `~/workspace/artifacts/data/YYYY-MM-DD-[slug].xlsx`

## Style Constants

```python
import xlsxwriter

wb = xlsxwriter.Workbook(path)
ws = wb.add_worksheet("Data")

h_fmt = wb.add_format({
    "bold": True, "font_color": "#FFFFFF", "bg_color": "#0D1B3E",
    "align": "center", "valign": "vcenter", "border": 1,
})
section_fmt = wb.add_format({
    "bold": True, "font_color": "#FFFFFF", "bg_color": "#1E3A5F",
    "valign": "vcenter",
})
row_fmt = wb.add_format({"bottom": 1, "border_color": "#E5E7EB"})
pct_pos = wb.add_format({"font_color": "#16A34A", "num_format": "0.00%", "bottom": 1, "border_color": "#E5E7EB"})
pct_neg = wb.add_format({"font_color": "#DC2626", "num_format": "0.00%", "bottom": 1, "border_color": "#E5E7EB"})
num_fmt = wb.add_format({"num_format": "#,##0.00", "bottom": 1, "border_color": "#E5E7EB"})
```

## Template 1: Simple Table

```python
COLUMNS = [
    ("date",       "Date",    14, None),
    ("value",      "Value",   12, "#,##0"),
    ("change_pct", "Change%", 12, "0.00%"),
]

for col_i, (key, label, width, _) in enumerate(COLUMNS):
    ws.write(0, col_i, label, h_fmt)
    ws.set_column(col_i, col_i, width)

for row_i, row in enumerate(DATA, 1):
    for col_i, (key, _, _, fmt) in enumerate(COLUMNS):
        val = row[key]
        if key.endswith(("_pct", "_change", "_growth")) and isinstance(val, (int, float)):
            cell_fmt = pct_pos if val >= 0 else pct_neg
        elif fmt:
            cell_fmt = wb.add_format({"num_format": fmt, "bottom": 1, "border_color": "#E5E7EB"})
        else:
            cell_fmt = row_fmt
        ws.write(row_i, col_i, val, cell_fmt)

ws.freeze_panes(1, 0)
wb.close()
```

## Template 2: Table + Chart (compact 4:3)

Phase 1: write all cells. Phase 2: insert charts. Never mix.

```python
# After writing data, determine chart placement:
last_data_row = <max row written>
last_data_col = <max col written>

chart_row = 1 if last_data_col <= 4 else last_data_row + 1
chart_col = last_data_col + 2 if last_data_col <= 4 else 1

chart = wb.add_chart({"type": "line"})  # or "column", "bar", "pie", "scatter", "area", "radar"
chart.add_series({
    "name": "Series Name",
    "categories": "=Data!$A$2:$A$10",  # 1-based Excel notation
    "values":     "=Data!$B$2:$B$10",
})
chart.set_size({"width": 400, "height": 300})  # always 4:3
chart.set_title({"name": "Chart Title", "name_font": {"size": 10}})
chart.set_plotarea({"layout": {"x": 0.18, "y": 0.12, "width": 0.72, "height": 0.68}})
chart.set_legend({"position": "bottom"})

ws.insert_chart(chart_row, chart_col, chart)
wb.close()
```

## Chart Type → `"type"` value

| Goal | type |
|------|------|
| Trend over time | `"line"` |
| Category comparison | `"column"` (vertical) |
| Horizontal comparison | `"bar"` |
| Composition | `"pie"` |
| Correlation | `"scatter"` |
| Volume/cumulative | `"area"` |
| Multi-metric profile | `"radar"` |
