# Raw Movie Dataset

This folder contains the original dataset used as the starting point for the Global Movie Success Analysis project.

## Dataset Overview

The dataset contains movie-level information covering financial performance, ratings, genres, cast and crew, awards, popularity and movie classification flags.

| Attribute | Details |
|---|---|
| Dataset | Global Movies Dataset |
| Source | Kaggle |
| Coverage | 1950–2026 |
| Records | 100,000 |
| Columns | 27 |
| Format | CSV |

## Data Source

The original dataset was obtained from Kaggle:

[Global Movies Dataset 1950–2026](https://www.kaggle.com/datasets/suhanigupta04/global-movies-dataset-19502026/data)

## File

`global_movies_dataset_1950_2026(1).csv`

## Dataset Fields

### Movie Information

- `movie_id`
- `title`
- `release_year`
- `decade`
- `runtime_min`

### Genre & Classification

- `genre`
- `subgenre`
- `blockbuster_flag`
- `franchise_flag`
- `top_100_prob`

### Cast & Crew

- `director`
- `lead_actor`
- `lead_actress`

### Location & Language

- `country`
- `language`

### Ratings & Popularity

- `imdb_rating`
- `votes`
- `popularity_score`
- `metascore`
- `audience_score`

### Financial Performance

- `budget_million`
- `marketing_budget_million`
- `revenue_million`
- `roi_pct`

### Awards & Distribution

- `award_nominations`
- `award_wins`
- `streaming_platform`

## Purpose

This raw dataset was used as the starting point for the project.

The data was then prepared and analyzed using Python before being used for the final Power BI analysis.

## Data Workflow

```text
Kaggle Raw Dataset
        ↓
Python Data Cleaning & EDA
        ↓
Outlier / Revenue Analysis
        ↓
Cleaned Analysis-Ready Dataset
        ↓
Power BI Dashboard
