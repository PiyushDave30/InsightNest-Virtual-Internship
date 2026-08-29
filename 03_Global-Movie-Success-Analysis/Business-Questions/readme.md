# Business Question Analysis

This folder contains the supporting analysis and visuals used to answer the four business questions of the Global Movie Success Analysis project.

The analysis combines Python-based data preparation with Power BI visualizations to identify important patterns in movie revenue, profit, audience reception and crew performance.

---

## Project Presentation

[📊 View the Final Project Presentation](Movie%20Analysis.pptx)

The presentation contains the complete project story, including the business questions, methodology, analysis, key findings and recommendations.

---

# Q1. Does a higher budget lead to greater box office revenue?

### Supporting Visual

![Q1 Budget vs Revenue](Q1%20Budget%20vs%20Revenue.png)

### Key Finding

Higher-budget movies generally tend to generate higher revenue, showing a positive relationship between budget and box-office performance. However, the wide spread of the points shows that a higher budget does not always guarantee higher commercial success.

### Business Takeaway

Budget is an important investment factor, but movie decisions should also consider other factors such as genre, audience reception and talent performance.

---

# Q2. Which movie genres generate the highest revenue?

### Revenue by Genre

![Q2 Revenue vs Genre](Q2%20Rev%20vs%20Genre.png)
---

### Profit by Genre

![Q2 Profit vs Genre](Q2.1%20Profit%20vs%20Genre.png)

### Key Finding

Sci-Fi, Fantasy and Adventure are the leading genres across both total revenue and total profit. The revenue and profit rankings are very similar, with only small changes among the lower-ranked genres.

### Business Takeaway

Both revenue and profit should be considered when evaluating genres, as high revenue does not always result in the same level of profitability.

---

# Q3. Is there a relationship between audience ratings and commercial success?

### IMDb Rating vs ROI

![Q3 IMDb Rating vs ROI](Q3%20imdb%20rating%20vs%20ROI.png)
---

### Audience Score vs Revenue

![Q3 Audience Score vs Revenue](Q3.1%20Audience%20Score%20vs%20Revenue.png)
---

### Audience Score vs ROI

![Q3 Audience Score vs ROI](Q3.2%20Audience%20Score%20vs%20ROI.png)

### Key Finding

Higher audience scores generally show an association with higher revenue, while IMDb ratings show a positive relationship with ROI. However, the points are widely spread, so ratings alone cannot determine a movie's commercial success.

### Business Takeaway

Audience reception and ratings can be useful supporting indicators, but they should be considered together with financial and other business factors.

---

# Q4. Which directors or actors consistently deliver successful movies?

Q4 evaluates crew performance using **average capped revenue and standard deviation**.

A lower standard deviation indicates lower revenue variation and therefore more consistent performance.

---

## Director Performance

![Q4 Director Performance](Q4%20Director%20Performance.png)

### Key Finding

Patty Jenkins has the highest average capped revenue, showing strong commercial performance. However, the higher standard deviation indicates greater revenue variation. Sofia Coppola has comparatively lower revenue but more stable performance because of lower revenue variation.

---

## Actor Performance

![Q4 Actor Performance](Q4.1%20ActorPerformance.png.png)

### Key Finding

Emma Stone has the highest average capped revenue, showing strong commercial performance. However, the higher standard deviation indicates greater revenue variation. Brad Pitt has comparatively lower revenue but more stable performance because of lower revenue variation.

### Overall Q4 Finding

The analysis shows that high average revenue does not always mean consistent performance. Average capped revenue helps identify stronger commercial performers, while standard deviation helps identify performers with more stable revenue.

### Business Takeaway

Actors and directors should be evaluated using both commercial performance and consistency rather than relying only on average revenue.

---

# Business Question Summary

| Business Question | Analysis Used | Main Visual |
|---|---|---|
| Q1 | Budget vs Revenue | Scatter Plot |
| Q2 | Revenue & Profit by Genre | Bar Charts |
| Q3 | Ratings vs Commercial Performance | Scatter Plots |
| Q4 | Crew Performance & Revenue Consistency | Tables & Bar Charts |

---

# Analysis Approach

The project followed a structured analytical workflow:

**Kaggle Raw Dataset → Python Cleaning & EDA → Cleaned Analysis-Ready Dataset → Power BI Dashboard → Business Insights**

### Python

Python was used for:

- Data cleaning
- Exploratory Data Analysis (EDA)
- Outlier analysis
- Revenue capping for crew consistency analysis
- Supporting analysis and visualization

### Power BI

Power BI was used for:

- Data modeling
- DAX calculations
- Interactive dashboards
- Business question analysis
- Financial and performance visualizations

---

# Key Analytical Areas

### Financial Performance

Analysis of:

- Budget
- Revenue
- Marketing Budget
- Profit
- ROI

### Genre Performance

Comparison of movie genres using:

- Total Revenue
- Total Profit

### Audience & Ratings

Analysis of:

- IMDb Rating
- Audience Score
- Revenue
- ROI

### Crew Performance

Evaluation of directors and actors using:

- Total Movies
- Average Revenue
- Average Capped Revenue
- Standard Deviation
- Revenue Consistency

---

| File | Type | Description |
|---|---|---|
| [`Movie Analysis Final Presentation`](Movie%20Analysis.pptx) | PPT | Final project presentation |
| [`Q1 Budget vs Revenue(1).png`](Q1%20Budget%20vs%20Revenue.png) | Image | Q1 supporting visual |
| [`Q2 Rev vs Genre.png`](Q2%20Rev%20vs%20Genre.png) | Image | Q2 revenue analysis |
| [`Q2.1 Profit vs Genre.png`](Q2.1%20Profit%20vs%20Genre.png) | Image | Q2 profit analysis |
| [`Q3 imdb rating vs ROI.png`](Q3%20imdb%20rating%20vs%20ROI.png) | Image | Q3 IMDb rating and ROI analysis |
| [`Q3.1 Audience Score vs Revenue.png`](Q3.1%20Audience%20Score%20vs%20Revenue.png) | Image | Q3 audience score and revenue analysis |
| [`Q3.2 Audience Score vs ROI.png`](Q3.2%20Audience%20Score%20vs%20ROI.png) | Image | Q3 audience score and ROI analysis |
| [`Q4 Director Performance.png`](Q4%20Director%20Performance.png) | Image | Q4 director consistency analysis |
| [`Q4.1 ActorPerformance.png.png`](Q4.1%20ActorPerformance.png.png) | Image | Q4 actor consistency analysis |

---
# Conclusion

The analysis shows that movie success depends on multiple factors rather than a single metric.

Budget is positively associated with revenue, Sci-Fi, Fantasy and Adventure show strong financial performance, audience reception has a positive association with revenue, and crew performance should be evaluated using both commercial results and consistency.

The combination of **Python, Power BI and business-focused analysis** provides a complete view of movie commercial performance.
