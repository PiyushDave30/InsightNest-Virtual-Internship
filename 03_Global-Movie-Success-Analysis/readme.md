# 🎬 Global Movie Success Analysis

> **Understanding the factors associated with commercial success**

A collaborative data analytics project that analyzes **100,000 movie records covering 1950–2026** to understand the factors associated with movie commercial success.

The project combines **Python for data cleaning, exploratory data analysis and supporting analysis** with **Power BI for data modeling, interactive visualization and business-question analysis**.

---

## 👥 Team

### Team 3 — InsightNest

| Member | Role / Contribution |
|---|---|
| **Keshav Baheti** | Python data cleaning, EDA, outlier/revenue analysis and supporting crew analysis |
| **Piyush Dave** | Power BI dashboard development, DAX, visualization and business-question analysis |

This project was completed collaboratively. Python was used to prepare and explore the data, while Power BI was used to build the final interactive analytical dashboard.

---

# 📌 Project Overview

Movie success is influenced by multiple factors such as financial investment, genre, audience reception and talent.

The objective of this project was to analyze movie data and identify patterns associated with commercial success rather than relying on a single performance metric.

The analysis focuses on four key business questions:

1. **Does a higher budget lead to greater box office revenue?**
2. **Which movie genres generate the highest revenue?**
3. **Is there a relationship between audience ratings and commercial success?**
4. **Which directors or actors consistently deliver successful movies?**

The findings were converted into business-oriented insights and recommendations.

---

# 🎯 Project Objective

The project aims to:

- Understand the relationship between movie budget and revenue
- Identify high-performing movie genres
- Analyze the relationship between audience ratings and commercial performance
- Evaluate actor and director performance
- Study revenue consistency using variation and standard deviation
- Convert analytical findings into practical business recommendations

---

# 📊 Dataset

The project uses the **Global Movies Dataset (1950–2026)** obtained from Kaggle.

| Attribute | Details |
|---|---|
| Source | Kaggle |
| Dataset | Global Movies Dataset |
| Period | 1950–2026 |
| Records | 100,000 |
| Raw Dataset | 27 columns |
| Cleaned Dataset | 30 columns |
| Format | CSV |

### 🔗 Dataset Source

[View Global Movies Dataset on Kaggle](https://www.kaggle.com/datasets/suhanigupta04/global-movies-dataset-19502026/data)

### Key Fields

The dataset contains information related to:

- Budget
- Marketing Budget
- Revenue
- Profit
- ROI
- Genre
- Sub-genre
- IMDb Rating
- Audience Score
- Meta Score
- Director
- Lead Actor
- Lead Actress
- Release Year
- Popularity
- Awards
- Blockbuster Flag
- Franchise Flag

---

# 🔄 End-to-End Project Workflow

The complete project follows this workflow:

```text
                    ┌─────────────────────────┐
                    │   Kaggle Raw Dataset    │
                    │   100,000 Movies        │
                    │   1950–2026             │
                    └────────────┬────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │      Python Stage       │
                    │                         │
                    │ • Data Cleaning         │
                    │ • EDA                   │
                    │ • Outlier Analysis      │
                    │ • Revenue Analysis      │
                    │ • Revenue Capping       │
                    └────────────┬────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │ Cleaned Analysis-Ready  │
                    │ Dataset                 │
                    │                         │
                    │ • Profit                │
                    │ • ROI                   │
                    │ • Revenue Capped        │
                    └────────────┬────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │      Power BI Stage     │
                    │                         │
                    │ • Data Modeling         │
                    │ • DAX Calculations      │
                    │ • Interactive Visuals   │
                    │ • Dashboard             │
                    └────────────┬────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │   Business Questions    │
                    │                         │
                    │ Q1 • Q2 • Q3 • Q4       │
                    └────────────┬────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │ Findings &              │
                    │ Recommendations         │
                    └─────────────────────────┘
