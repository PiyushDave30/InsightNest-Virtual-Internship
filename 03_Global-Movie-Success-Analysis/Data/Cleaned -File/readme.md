# Cleaned Movie Dataset

This folder contains the cleaned and analysis-ready version of the Global Movies Dataset used for the project analysis.

## Dataset Overview

The cleaned dataset retains the original 100,000 movie records and includes additional calculated fields used during the analysis.

| Attribute | Details |
|---|---|
| Dataset | Global Movies Dataset |
| Records | 100,000 |
| Original Columns | 27 |
| Cleaned Dataset Columns | 30 |
| Coverage | 1950–2026 |
| Format | CSV |

## File

[Cleaned Data File](Python_Cleaned_Data.csv)

## Data Preparation

Python was used to prepare the dataset for analysis.

The preparation included:

- Missing-value checks
- Duplicate checks
- Data-type checks
- Derived measures
- Exploratory Data Analysis (EDA)
- Outlier / revenue analysis
- Preparation of the analysis-ready dataset

## Additional Fields

Compared with the raw dataset, the cleaned file contains three additional fields:

| Field | Purpose |
|---|---|
| `profit` | Used to analyze movie profitability |
| `roi` | Used for return-on-investment analysis |
| `revenue_capped` | Used to reduce the influence of extreme revenue values during crew analysis |

## Revenue Capping

Revenue contained extreme values that could strongly influence actor and director comparisons.

Therefore, a capped revenue field was created for the crew analysis to reduce the impact of extreme observations.

This helped provide a more balanced basis for comparing crew performance.

## Main Analysis Areas

The cleaned dataset supports analysis of:

### Financial Performance

- Budget
- Marketing Budget
- Revenue
- Profit
- ROI

### Genre Performance

- Genre
- Subgenre
- Revenue
- Profit

### Audience & Ratings

- IMDb Rating
- Audience Score
- Meta Score
- Popularity

### Crew Performance

- Director
- Lead Actor
- Lead Actress
- Revenue
- Capped Revenue
- Profit
- ROI

### Awards & Movie Classification

- Award Nominations
- Award Wins
- Blockbuster Flag
- Franchise Flag
- Top 100 Probability

## Data Workflow

```text
Raw Kaggle Dataset
        ↓
Data Cleaning
        ↓
EDA
        ↓
Outlier / Revenue Analysis
        ↓
Revenue Capping for Crew Analysis
        ↓
Cleaned Analysis-Ready Dataset
        ↓
Power BI Analysis
