# 📊 Power BI File

This folder contains the full interactive dashboard and a static export for quick viewing.

## Files

**`NovaKart_Analysis.pbix`**
The complete, interactive Power BI report — data model, Power Query transformations, all DAX measures, and all 6 dashboard pages.

**`NovaKart_Analysis.pdf`**
A static, page-by-page export of the full dashboard for anyone without Power BI Desktop installed.

## Data Model 

Four fact/dimension tables plus a dedicated date table, connected as follows:

```
Products (1) ──< Orders (many) >── Customers (1)
                     │
                     └──< Returns (many, via order_id)

Date_Table (1) ──< Orders (many, via order_date)
```

- **Orders** is the central fact table — one row per order line
- **Products** and **Customers** are dimension tables joined via Left Outer relationships (chosen deliberately so orders with missing/orphan references aren't silently dropped)
- **Returns** connects to Orders on `order_id`, with cross-filter direction set to Both so category- and channel-level filters correctly propagate into return-rate calculations
- **Date_Table** enables time intelligence measures (YoY growth, monthly trends)

## Report Pages

| Page | Contents |
|---|---|
| **Home** | Project overview, key stats, navigation to all report pages |
| **Executive Summary** | Core KPIs — Net Revenue, Order Count, AOV, Gross Profit, Margin %, Cancellation Rate; monthly trend, category breakdown, top products/channels/cities |
| **Sales & Trend** | YoY growth, seasonality (Oct–Nov spike), category margin vs revenue, top states, payment methods, segment revenue split |
| **Delivery & Returns** | Return rate by category/sub-category, top return reasons, delivery-speed vs return-rate correlation, Metro vs Tier-2 delivery gap, channel delivery comparison, COD vs cancellation |
| **Customer & Channel** | Segment comparison (AOV/orders/revenue), discount band vs AOV, top customers, channel order share, repeat vs new customer split, full 4-metric channel profile table |
| **Recommendation** | Founder's Q40 answer — problem, recommendation, money at stake, number to track, supporting channel comparison |

## Key DAX Measures (by category)

- **Revenue & Profit:** Net Revenue, Gross Profit, Margin %, AOV, Total Gross Revenue
- **Growth & Seasonality:** YoY Growth %, Oct–Nov Revenue Share %
- **Delivery:** Avg Delivery Days, delivery breakdowns by channel and city tier
- **Returns:** Return Rate %, Return Count, category/sub-category return breakdowns
- **Customers:** Repeat Customer %, Top 20% Revenue Share %, segment-level AOV and revenue
- **Cancellations:** Cancellation Rate %, Cancelled Revenue

All measures were built from first principles in DAX (not just drag-and-drop visual aggregations), so the logic behind every number is transparent and auditable directly in the file.

## How to Open

1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free, Windows only)
2. Open `NovaKart_Analysis.pbix`
3. Use the left sidebar or the Home page tiles to navigate between report pages
4. All measures are visible and editable in the **Data** and **Model** views if you want to inspect the underlying DAX

Full page-by-page findings and write-up are in the [main project README](../README.md).
