# Ecommerce Analytics Dashboard

A 6-page Power BI dashboard that turns 1,000 raw ecommerce transaction records into a decision-support tool — answering four real business questions around sales, customers, returns, and marketing.

![Home Page](Screenshots/1_Home.png)

## Core Idea

This project turns 1,000 raw ecommerce transaction records into a 6-page Power BI dashboard that answers 4 real business questions — where the money is made, who the best customers are, why returns happen, and which marketing channel is worth the spend. The goal was to build a decision-support tool — not just charts, but a dashboard where a manager could look at any page and immediately know what action to take next, whether that's capping discounts, improving retention, or reducing returns.

## Problem Statement

An ecommerce company has raw data on sales, customers, returns, and marketing, but no centralized dashboard to support quick decision-making. This project identifies four business questions any ecommerce company would realistically ask, and builds a dashboard around answering each one with real, verified data covering **January 2024 to December 2025**.

## Business Questions Solved

| # | Question | Key Finding |
|---|---|---|
| 1 | Which categories and products drive revenue vs. profit, and where are we discounting so hard that orders turn negative? | Electronics drives **53.23%** of revenue but only **30.84%** of profit. Discounts above **20%** consistently push orders into a net loss. |
| 2 | Who are our highest-value customers, and how much of revenue comes from repeat buyers vs. one-timers? | **275 of 326 customers (84%)** are repeat buyers, generating **95.2%** of total revenue. |
| 3 | What's driving returns, and which categories or shipping modes are hurting net profit once returns are factored in? | **Fashion** has the highest return rate at **14.16%**, more than double any other category. Returns cost **7.18%** of total profit. |
| 4 | Which marketing channel acquires the most valuable orders, and how should Q4 seasonality shape inventory and spend? | **Organic Search** is the top channel (₹62.7K revenue). **December** is the peak sales month, signaling Q4 demand. |

## Dashboard Structure

| Page | Purpose |
|---|---|
| **Home** | Landing/navigation page linking to all report pages |
| **Executive Overview** | High-level KPIs, monthly trend, revenue by category/country, region performance |
| **Revenue & Profit Analysis** | Category/sub-category/product profitability, discount-vs-profit relationship |
| **Customer Analysis** | Repeat vs. one-time buyers, customer segments, payment methods |
| **Return Orders Insight** | Return rate by category and shipping mode, profit lost to returns |
| **Marketing & Seasonal Analysis** | Channel performance, weekday vs. weekend, quarterly trend |

## Key Insights (Dataset-Wide)

- **Total Revenue:** ₹236.76K | **Total Profit:** ₹66.19K | **Total Orders:** 1,000 | **Total Customers:** 326
- **Profit Margin:** 27.96% | **Return Rate:** 8.20%
- Electronics leads revenue (53.23%) but trails in profit share (30.84%) — a clear revenue-profit mismatch
- Orders with 0% discount contributed the most profit; profit turns negative once discounts exceed ~20%
- 95.2% of revenue comes from repeat customers, despite them being 84% of the customer base
- Fashion's return rate (14.16%) is more than double the next-highest category, Electronics (8.73%)
- Returns cost the business ₹18.37K in lost revenue and ₹5.12K in lost profit
- Organic Search is the strongest marketing channel by both revenue and profit; Affiliate is the weakest
- December is the peak revenue month, and weekday sales run roughly 2x weekend sales

## Tools & Skills Demonstrated

- **Power BI:** Data modeling, relationships, Date table for time intelligence
- **DAX:** Measures (SUM, DISTINCTCOUNT, CALCULATE, DIVIDE, ALLEXCEPT), calculated columns for custom business logic
- **Field Parameters:** Single-visual toggle between Revenue and Profit
- **Data Cleaning:** Null/duplicate checks, formula verification on calculated fields
- **Dashboard Design:** Consistent theme, slicers, KPI cards, multi-page navigation

## Repository Structure

```
├── Ecommerce_Dashboard.pbix       Power BI file
├── raw-data/                      Raw dataset + data dictionary
├── screenshots/                   Dashboard page images
└── power-bi-file/                 DAX measures & technical documentation
```

## How to Use

1. Download `Ecommerce_Dashboard.pbix`
2. Open in Power BI Desktop (free download from Microsoft)
3. Navigate using the Home page, or the page tabs at the bottom

---
*Built as part of a Data Analyst portfolio project. Dataset: 1,000 ecommerce transaction records, Jan 2024 – Dec 2025.*
