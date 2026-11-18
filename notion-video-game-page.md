## Overview

Analyzed 16,597 video game titles to help a publisher decide which genres to prioritize in each region (North America, Europe, Japan, Other).

## Business Questions

1. Which genres are the biggest markets in each region?
2. Which genres perform best per title, not just in total?
3. How different are regional tastes?
4. How concentrated are sales among publishers?

## Data & Tools

| Item | Detail |
|---|---|
| Data | Public video game sales dataset, 16,597 titles (1980 to 2020) |
| Measure | Units sold in millions (not revenue) |
| Cleaning | Removed 1 duplicate, handled 271 missing years and 58 missing publishers |
| Tools | Python, pandas, NumPy, Matplotlib |
| Techniques | groupby aggregation, mean vs median comparison, share analysis, heatmap |

## Key Findings

- **Action is the largest market** (1,751M units, 19.6% of global), but ranks only 7th of 12 genres in sales per title. Its volume comes from releasing many titles (3,316).
- **Platform and Shooter perform best per title:** mean 0.94M and 0.79M units.
- **Japan has a different taste:** Role-Playing is 27.3% of Japanese sales vs about 7.5% elsewhere, while Shooter is only 3.0% vs about 13% elsewhere.
- **North America, Europe and Other regions look alike:** Action 20% to 24%, Sports 15% to 17%.
- **Nintendo leads in North America, Europe and Japan**, with 35.3% of Japan's sales.
- **Mean sales are 2.5 to 4 times the median** in every genre, so a few hits lift the average. I used the median to describe a typical title.

## Recommendations

1. Japan: lead with Role-Playing and avoid a Shooter-first plan.
2. North America and Europe: Action and Sports for volume; Shooter and Platform for stronger sales per title.
3. Deprioritize Strategy and Adventure for volume (lowest sales per title).

## Sample Code: Sales per Title by Genre

```python
per_title = (df.groupby('Genre')['Global_Sales']
               .agg(titles='count', mean='mean', median='median')
               .sort_values('mean', ascending=False))

share = totals[REGIONS].div(totals[REGIONS].sum()) * 100
```

## Limitations

Sales are units, not revenue. The analysis is descriptive, with no statistical tests, and the dataset thins out after 2015.

## Links

[View notebook & README on GitHub](GANTI-DENGAN-LINK-REPO-VIDEO-GAME)
