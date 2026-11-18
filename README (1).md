# Video Game Sales Analysis: Which Genres Win in Which Region?

Exploratory analysis of 16,597 video game titles (1980 to 2020) to help a publisher decide which genres to prioritize in each region. Built with Python (pandas, NumPy, Matplotlib).

**Notebook:** [`vgsales_analysis.ipynb`](vgsales_analysis.ipynb) (outputs and charts are saved in the file, so it renders directly on GitHub)

## Business questions

1. Which genres are the biggest markets in each region?
2. Which genres perform best per title, not just in total?
3. How different are regional tastes?
4. How concentrated are sales among publishers?

## Data

`data/vgsales.csv`: one row per title, with release year, genre, publisher, and sales in **millions of units** for North America, Europe, Japan, Other regions, and Global. Sales are units, not revenue.

**Cleaning:** removed 1 exact duplicate row; kept 271 titles with no release year (excluded only from the yearly trend); labeled 58 missing publishers as `Unknown`; limited the trend to 1995 to 2015 because 2016 looks incomplete and 2017 to 2020 contain only 4 titles.

## Key findings

| # | Finding | Figures |
|---|---|---|
| 1 | **Action is the largest market** overall, but its volume comes from releasing many titles, not from strong sales per title | 1,751M units (19.6% of global); 3,316 titles; mean 0.53M per title, 7th of 12 |
| 2 | **Platform and Shooter perform best per title** | Platform: mean 0.94M, median 0.28M. Shooter: mean 0.79M, median 0.23M |
| 3 | **Japan has a different taste.** Role-Playing leads there, and Shooter is weak | Role-Playing: 27.3% of Japan's sales vs about 7.5% elsewhere. Shooter: 3.0% vs about 13% elsewhere |
| 4 | **North America, Europe and Other regions look alike** | Action 20% to 24%, Sports 15% to 17%, Shooter about 13% |
| 5 | **Nintendo is the top publisher in North America, Europe and Japan** | 35.3% of Japan's sales vs 18.6% in North America and 17.2% in Europe |
| 6 | **Sales peak with 2008 releases**, then decline within this dataset | 679M units in 2008 |

In every genre the mean sales per title is roughly 2.5 to 4 times the median, so a few hits lift the average. The median is a better picture of a typical title.

## Charts

| | |
|---|---|
| ![Total sales](charts/01_total_sales_by_genre_region.png) | ![Per title](charts/02_sales_per_title_by_genre.png) |
| ![Genre share](charts/03_genre_share_by_region.png) | ![Trend](charts/04_global_sales_by_year.png) |

## Recommendations

- **Japan:** lead with Role-Playing, and avoid a Shooter-first plan.
- **North America and Europe:** Action and Sports are the biggest markets, so they suit a publisher that can release many titles. With a tight budget, Shooter and Platform give stronger sales per title.
- **Low priority for volume:** Strategy and Adventure sit near the bottom of the totals in every region and have the lowest sales per title.
- Plan a separate release mix for Japan instead of reusing the Western plan.

## Limitations

- Sales are units, not revenue. There are no prices, costs or profit figures.
- Per-title averages depend on which titles are in the dataset and how many titles each genre releases.
- Regional taste also reflects platforms and publishers (for example Nintendo hardware), not genre alone.
- The dataset thins out after 2015, and the 2008 peak may partly reflect how the data was collected (for example, digital sales may not be captured).
- The analysis is descriptive. No statistical tests were run, so differences are patterns, not proven effects.

## How to run

```bash
pip install -r requirements.txt
jupyter notebook vgsales_analysis.ipynb
```

Run the notebook from this folder so the `data/` and `charts/` paths resolve.
