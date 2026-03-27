# Matplotlib Chart Reference

## Base Setup (include in every script)

```python
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

sns.set_style('white')

plt.rcParams['font.sans-serif'] = [
    'Noto Sans CJK SC', 'Noto Sans CJK TC',
    'PingFang SC', 'Heiti SC', 'DejaVu Sans'
]
plt.rcParams['axes.unicode_minus'] = False
plt.rcParams.update({
    'figure.facecolor': 'white',
    'axes.facecolor': 'white',
    'axes.spines.right': False,
    'axes.spines.top': False,
    'axes.grid': False,
    'figure.dpi': 150,
    'savefig.dpi': 150,
    'savefig.bbox': 'tight',
    'savefig.facecolor': 'white',
    'savefig.edgecolor': 'none',
})

# Nicole's palette
PRIMARY   = '#4A90A4'
ACCENT    = '#E07B54'
SUCCESS   = '#6B9B7A'
WARNING   = '#D4A84B'
NEUTRAL   = '#8B9298'
SERIES    = [PRIMARY, ACCENT, SUCCESS, WARNING, NEUTRAL, '#8B7CB8']
```

## Bar Chart

```python
def bar_chart(categories, values, title, ylabel, save_path, highlight_idx=None):
    fig, ax = plt.subplots(figsize=(10, 6))
    colors = [ACCENT if i == highlight_idx else PRIMARY for i in range(len(categories))]
    width = 0.5 if len(categories) >= 4 else 0.35
    bars = ax.bar(categories, values, width=width, color=colors, edgecolor='none')

    for bar, val in zip(bars, values):
        ax.text(bar.get_x() + bar.get_width()/2, bar.get_height() + max(values)*0.02,
                f'{val:,.0f}', ha='center', va='bottom', fontsize=11)

    ax.set_ylabel(ylabel, fontsize=12)
    ax.set_title(title, fontsize=14, fontweight='bold', pad=15)
    ax.set_ylim(0, max(values) * 1.15)

    if len(categories) > 5 or max(len(str(c)) for c in categories) > 8:
        plt.xticks(rotation=45, ha='right')
        plt.subplots_adjust(bottom=0.2)

    plt.tight_layout()
    plt.savefig(save_path)
    plt.close()
```

`highlight_idx`: index of the "hero" bar to show in accent color. Default: None (all primary color).

## Line Chart

```python
def line_chart(x, y, title, xlabel, ylabel, save_path, fill=True):
    fig, ax = plt.subplots(figsize=(10, 6))
    ax.plot(x, y, marker='o', markersize=8, color=PRIMARY, linewidth=2,
            markerfacecolor='white', markeredgewidth=2, markeredgecolor=PRIMARY)
    if fill:
        ax.fill_between(x, y, alpha=0.15, color=PRIMARY)

    for xi, yi in zip(x, y):
        ax.text(xi, yi + (max(y)-min(y))*0.05, f'{yi:,.1f}',
                ha='center', va='bottom', fontsize=10)

    ax.set_xlabel(xlabel, fontsize=12)
    ax.set_ylabel(ylabel, fontsize=12)
    ax.set_title(title, fontsize=14, fontweight='bold', pad=15)
    ax.set_ylim(min(y)*0.9, max(y)*1.15)
    plt.tight_layout()
    plt.savefig(save_path)
    plt.close()
```

## Saving

```python
plt.tight_layout()
plt.savefig(
    '/Users/mac/.openclaw/workspace/artifacts/charts/YYYY-MM-DD-slug.png',
    facecolor='white', edgecolor='none', bbox_inches='tight', dpi=150
)
plt.close()
```

## Troubleshooting

| Issue | Fix |
|-------|-----|
| CJK garbled | Verify Noto Sans CJK fonts: `fc-list | grep -i noto` |
| Label overlap | `plt.tight_layout()` + increase figsize |
| X-labels crowded | `rotation=45, ha='right'` + `subplots_adjust(bottom=0.2)` |
| Labels cut off at top | `ax.set_ylim(min_val, max_val * 1.15)` |
| Legend covers data | `bbox_to_anchor=(1.02, 1), loc='upper left'` |
