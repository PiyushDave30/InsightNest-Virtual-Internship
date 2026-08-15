# Ecommerce Analytics Dashboard

A 6-page Power BI dashboard that turns 1,000 raw ecommerce transaction records into a decision-support tool — answering four real business questions around sales, customers, returns, and marketing.

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

## Dashboard Walkthrough

### 1. Home
Landing page with navigation cards linking to all six report pages, giving a quick overview of what each page covers before diving in.

![Home](Screenshots/1.%20Home.png)

---

### 2. Executive Overview
A business-wide snapshot before drilling into specific questions. **KPIs:** Total Revenue (₹236.76K), Total Profit (₹66.19K), Total Orders (1,000), Total Customers (326), Profit Margin (27.96%), Return Rate (8.20%). Includes a monthly revenue & profit trend, revenue by country, revenue & profit by region, and a country/city performance table.

![Executive Overview](Screenshots/2.%20Executive%20Overview.png)

---

### 3. Revenue & Profit Analysis
**Answers Business Question 1.** A Field Parameter toggle switches a chart between Total Revenue and Total Profit by sub-category. Also shows profit by category and payment method, top 5 / bottom 5 products by profit, and a discount-bucket chart that pinpoints the exact discount level (~20%) where profit turns negative.

![Revenue & Profit Analysis](Screenshots/3.%20Revenue%20&%20Profit%20Analysis.png)

---

### 4. Customer Analysis
**Answers Business Question 2.** Breaks customers down by payment method, customer type (Repeat: 275 vs. One-time: 51), and segment (Consumer/Corporate/Home Office). The revenue-by-customer-type chart shows repeat buyers alone account for 95.2% of total revenue.

![Customer Analysis](Screenshots/4.%20Customer%20Analysis.png)

---

### 5. Return Orders Insight
**Answers Business Question 3.** Return rate by category (Fashion highest at 14.16%), profit vs. loss-profit by category, a monthly orders-vs-returns trend, and a shipping-mode performance table covering return rate, delivery days, shipping cost, and profit margin side by side.

![Return Orders Insight](Screenshots/5.%20Return%20Orders.png)

---

### 6. Marketing & Seasonal Analysis
**Answers Business Question 4.** Revenue and profit by marketing channel (Organic Search leads), average order value by channel and segment, weekday vs. weekend performance, and a quarterly revenue trend that highlights the Q4 seasonal spike.

![Marketing & Seasonal Analysis](Screenshots/6.%20Marketing%20&%20Seasonal%20Insights.png)

---

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

- **Power BI:** Data modeling, table relationships, a standalone Date table for time intelligence
- **DAX:** Measures built with `SUM`, `DISTINCTCOUNT`, `CALCULATE`, `DIVIDE`, `ALLEXCEPT`; calculated columns for custom business logic (Discount Bucket, Customer Type)
- **Field Parameters:** A single-visual toggle between Revenue and Profit, instead of duplicating charts
- **Data Cleaning:** Null/duplicate checks and manual formula verification on every calculated field before building any visual
- **Dashboard Design:** Consistent theme and slicers across all pages, redundant visuals identified and removed, chart types chosen for readability over appearance

## Repository Structure

```
├── README.md                      This file
├── raw-data/                      Raw dataset + data dictionary
├── Screenshots/                   Dashboard page images
└── power-bi-file/                 .pbix file, dashboard PDF export, and technical documentation
```

## How to Use

1. Download the `.pbix` file from the `power-bi-file/` folder
2. Open in Power BI Desktop (free download from Microsoft)
3. Navigate using the Home page, or the page tabs at the bottom
4. No Power BI installed? Open the dashboard PDF export in the same folder for a static view

---
*Built as part of a Data Analyst portfolio project. Dataset: 1,000 ecommerce transaction records, Jan 2024 – Dec 2025.*
