# Power BI File — Technical Documentation

Documentation for the files in this folder.

## Files in This Folder

| File | Description |
|---|---|
| [Ecommerce Analysis](Ecommerce%20Analysis.pbix) | The full Power BI file — open in Power BI Desktop to explore interactively |
| [Ecommerce Analysis Dashboard PDF](Ecommerce%20Analysis.pdf) | Static export of all 6 pages, for quick viewing without Power BI installed |
| Screenshot | Reference image of the dashboard used in documentation |

## Data Model

| Table | Type | Purpose |
|---|---|---|
| `ecommerce` | Fact table | 1,000 imported rows from `ecommerce.csv` |
| `Date Table` | Dimension table | Standalone date table, marked as a Date table, related to `ecommerce[order_date]` for time intelligence |
| `Measures Tabele` | Empty/helper table | Holds all DAX measures separately from data columns, for easier navigation in the Fields pane |
| `Sales vs Profit Metric` | Field Parameter table | Powers the Revenue/Profit toggle on the Revenue & Profit Analysis page |

The model uses a single fact table with a one-to-many relationship from `Date` to `ecommerce`. No snowflake or star-schema dimensions were needed given the flat structure of the source data.

## Measures — What They Cover

Rather than listing every formula, here's what each group of measures does and why it exists:

| Group | Examples | Purpose |
|---|---|---|
| **Base aggregations** | Total Revenue, Total Profit, Total Cost, Total Orders, Total Customers | Core numbers every page depends on |
| **Ratios** | Profit Margin %, Discount %, Average Order Value, Avg Selling Price | Convert raw totals into comparable, decision-ready percentages |
| **Returns** | Return Rate %, Profit Lost to Returns, Net Profit Excl Returns | Isolate the financial impact of returned orders |
| **Loss detection** | Loss Making Orders %, Avg Discount on Loss Orders | Flag exactly when discounting stops being profitable |
| **Customer value** | Revenue from Repeat Customers %, Revenue per Customer, Orders per Customer | Separate one-time buyers from repeat buyers |
| **Operations** | Total Shipping Cost, Avg Delivery Days | Cover the logistics side of the business |

Two DAX patterns are used repeatedly across these measures:
- **`DIVIDE()`** instead of the `/` operator everywhere a ratio is calculated, so a filter context with zero orders/revenue returns a blank instead of an error.
- **`CALCULATE()` with a boolean filter** (e.g. `ecommerce[is_returned] = TRUE`, `ecommerce[profit] < 0`) to isolate a subset of rows for measures like Return Rate % or Loss Making Orders %.

## Calculated Columns

Two calculated columns exist because the dashboard needed **new row-level labels** that a measure can't produce — a measure returns a number for the current filter context, but a chart axis or legend needs a fixed category per row.

- **Discount Bucket** — groups the continuous `discount_pct` column into readable ranges (0%, 1–10%, 11–20%, etc.), used to show the exact point where discounting turns unprofitable, since a scatter plot of 1,000 raw points was unreadable.
- **Customer Type** — labels each customer as "Repeat" or "One-time" based on their total order count, calculated using `ALLEXCEPT` so the count reflects the customer's full order history rather than just the current row.

## Field Parameter

A Field Parameter named **Sales vs Profit Metric** lets one bar chart switch between `Total Revenue` and `Total Profit` via a slicer, instead of building two separate charts side by side. This keeps the Revenue & Profit Analysis page compact and adds a layer of interactivity beyond static visuals.

## Page-by-Page Breakdown

| Page | Visual Types Used | What It's Built To Show |
|---|---|---|
| Home | Navigation cards | Entry point linking to all report pages |
| Executive Overview | KPI cards, line chart, donut, bar chart, table | Business-wide snapshot before drilling into specific questions |
| Revenue & Profit Analysis | Parameter-driven bar chart, discount bucket bar chart, top/bottom product tables | Where profit is being made or lost, and at what discount threshold |
| Customer Analysis | Column charts, donut, table | Split between repeat and one-time buyers, and by customer segment |
| Return Orders Insight | Bar charts, donut, line chart, table | Which category/shipping mode drives returns and profit loss |
| Marketing & Seasonal Analysis | Bar charts, line chart | Channel performance and seasonal (Q4) demand pattern |

## Design Choices Worth Noting

- **Redundancy removed:** an earlier version of the Revenue & Profit page had both a matrix table and the parameter chart showing the same category-level numbers — the matrix was removed once it was clear it added no new information.
- **Chart type chosen for readability, not appearance:** a scatter plot was the first attempt to show discount vs. profit, but with 1,000 points it was unreadable; a bucketed bar chart replaced it because it answers the question in one glance.
- **Consistent slicers and color theme** are applied across pages so the report reads as one connected dashboard rather than five disconnected charts.
