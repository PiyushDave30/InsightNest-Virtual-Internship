# 🎬 Global Movie Success Analysis

**A movie studio wants to understand what drives commercial success.** This project investigates 100,000+ movies spanning 76 years (1950–2026) across four dimensions — budget, genre, audience reception, and talent performance — combining Python and Power BI to turn raw movie data into a business case study on what actually predicts a hit.

![Home](Screenshots/Home.png)

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-217346?style=flat)](https://learn.microsoft.com/en-us/dax/)

---

## 📑 Table of Contents

- [Project Purpose](#-project-purpose)
- [Data Source](#-data-source)
- [Collaboration](#-collaboration)
- [End-to-End Workflow](#-end-to-end-workflow)
- [Data Cleaning & Preparation](#-data-cleaning--preparation)
- [Revenue Capping & Outlier Analysis](#-revenue-capping--outlier-analysis)
- [Business Questions](#-business-questions)
- [Q1 — Budget vs Revenue](#q1--does-a-higher-budget-lead-to-greater-box-office-revenue)
- [Q2 — Genre Performance](#q2--which-movie-genres-generate-the-highest-revenue)
- [Q3 — Audience Ratings & Commercial Success](#q3--is-there-a-relationship-between-audience-ratings-and-commercial-success)
- [Q4 — Actor & Director Performance](#q4--which-directors-or-actors-consistently-deliver-successful-movies)
- [Understanding Standard Deviation](#-understanding-standard-deviation-in-simple-terms)
- [Power BI Dashboard](#-power-bi-dashboard)
- [Python Analysis](#-python-analysis)
- [Key Insights & Findings](#-key-insights--findings)
- [Business Recommendations](#-business-recommendations)
- [Problem Solved](#-problem-solved)
- [Final Conclusion](#-final-conclusion)
- [Repository Structure](#-repository-structure)
- [Project Deliverables](#-project-deliverables)
- [Connect](#-connect)

---

## 🎯 Project Purpose

The core business problem this project investigates:

> **"What factors are associated with movie commercial success?"**

Rather than treating this as a single question, the analysis breaks it into four testable dimensions:

1. **Financial investment** — Does a higher budget lead to greater box office revenue?
2. **Genre** — Which movie genres generate the highest revenue and profit?
3. **Audience reception** — Is there a relationship between audience ratings and commercial success?
4. **Crew/talent** — Which directors or actors consistently deliver successful movies?

Each question is answered using both Python (statistical/correlation analysis) and Power BI (interactive dashboard exploration), so every finding is verifiable from two independent angles.

---

## 📦 Data Source

**Global Movies Dataset 1950–2026** — [Kaggle](https://www.kaggle.com/datasets/suhanigupta04/global-movies-dataset-19502026/data)

- **100,000 movie records**
- **76 years of data** (1950–2026)
- **27 columns**, including:

| Field | Description |
|---|---|
| movie%20id, title | Movie identifiers |
| genre, subgenre | Genre tags (pipe-separated for multi-genre films; 1,885 distinct combinations, 51 distinct sub-genres) |
| release%20year | Year of release |
| budget%20million, revenue%20million | Financial figures (in millions) |
| roi%20pct | Return on investment, as provided in the source data |
| imdb%20rating, audience%20score, metascore | Critical and audience reception scores |
| director, lead%20actor, lead%20actress | Crew fields — drawn from a fixed pool of 10 directors and 12 actors/actresses |
| popularity%20score | Popularity metric |
| blockbuster%20flag, franchise%20flag | Boolean success indicators |
| award%20nominations, award%20wins | Awards data |
| top%20100%20prob | Probability of ranking in the top 100 |
| country, language, streaming%20platform | Distribution metadata |

**Data quality (verified directly from the raw file):** 0 missing values across all 27 columns, 0 duplicate rows, 0 duplicate `movie%20id` values. This dataset arrived clean at the structural level — the analytical work centered on deriving new fields and handling statistical outliers, not fixing broken data.

---

## 👥 Collaboration

This is a collaborative project — **Team 3, InsightNest**.

| Member | Contribution |
|---|---|
| **Keshav Baheti** | Python data cleaning, exploratory data analysis, outlier analysis, revenue analysis, supporting crew/talent analysis |
| **Piyush Dave** | Power BI dashboard development, data modelling, DAX, business-question analysis, visualization, dashboard presentation |

---

## 🧭 End-to-End Workflow

```
Kaggle Raw Dataset
        ↓
Python Data Cleaning
        ↓
Exploratory Data Analysis
        ↓
Outlier / Revenue Analysis
        ↓
Revenue Capping for Crew Analysis
        ↓
Cleaned Analysis-Ready Dataset
        ↓
Power BI Data Modelling
        ↓
DAX Calculations
        ↓
Interactive Power BI Dashboard
        ↓
Business Questions
        ↓
Insights & Findings
        ↓
Business Recommendations
        ↓
Final Presentation
```

**Why each stage matters:** the raw data was first inspected in Python to confirm its structural quality (no missing values, no duplicates). Exploratory analysis then examined the distribution and relationship of key fields — budget, revenue, ratings — to understand the shape of the data before drawing conclusions. Revenue outliers were investigated specifically because a handful of extreme-revenue films can distort an actor's or director's *average* performance, making one blockbuster look like a consistent pattern. Revenue capping was applied to correct for this before the crew/talent analysis. Only once the data was understood and prepared this way did the analysis move into Power BI for interactive dashboarding and the four core business questions.

---

## 🧹 Data Cleaning & Preparation

Performed in Python (`Global-Movie-Success-Analysis.ipynb`).

| Step | What Was Done | Why |
|---|---|---|
| Missing value check | `df.isna().sum()` confirmed **0 missing values** across all 27 columns | Establishes the dataset needs no imputation |
| Structural integrity check | Verified 0 duplicate rows and 0 duplicate `movie%20id` values | Confirms every row represents a unique movie |
| Data type inspection | `df.info()` used to confirm column types before analysis | Ensures numeric fields (budget, revenue, ratings) are treated correctly in calculations |
| Derived column — `profit` | Calculated as `revenue%20million − budget%20million` | The raw dataset provided revenue and budget separately; profit is not a native field |
| Derived column — `roi` | Calculated to support the Q3 (IMDb vs ROI) analysis | Used alongside the dataset's native `roi%20pct` field |
| Correlation analysis | `.corr()` computed for budget–revenue (Q1) and IMDb rating–ROI (Q3) | Quantifies the strength of each relationship rather than relying on visual inspection alone |
| Outlier detection | IQR method applied per director group on `revenue%20million` | Identifies how many extreme-revenue outliers exist within each director's filmography |
| Revenue capping | Outliers clipped to the 1.5×IQR bounds, per director group, producing a new `revenue%20capped` column | Prevents one or two blockbuster films from dominating a director's or actor's average — see next section |

Since the raw data had no missing values or duplicates to begin with, the "cleaning" effort in this project centered on **derivation and statistical treatment** rather than repair — a distinction worth being precise about.

---

## 📊 Revenue Capping & Outlier Analysis

**The problem:** revenue in this dataset contains extreme values. A director or actor with one or two blockbuster films can end up with an *average* revenue figure that doesn't represent their typical output — the blockbuster distorts the picture.

**The method:** using the standard 1.5×IQR (interquartile range) rule, revenue values were capped **within each director's own filmography**:

```python
def cap%20outliers%20iqr(group):
    Q1 = group.quantile(0.25)
    Q3 = group.quantile(0.75)
    IQR = Q3 - Q1
    lower%20bound = Q1 - 1.5 * IQR
    upper%20bound = Q3 + 1.5 * IQR
    return group.clip(lower=lower%20bound, upper=upper%20bound)

df["revenue%20capped"] = df.groupby("director")["revenue%20million"].transform(cap%20outliers%20iqr)
```

**In business terms:**

> **Without capping** — a few blockbuster movies can dominate a director's or actor's average revenue, making an inconsistent performer look artificially strong.
>
> **With capping** — the comparison becomes less dominated by a small number of extreme observations, giving a more balanced view of *typical* performance rather than best-case performance.

This capped revenue figure (`revenue%20capped`) is what powers the Crew Success page of the Power BI dashboard and the Q4 findings below.

---

## ❓ Business Questions

| Question | Main Analysis | Supporting Visual |
|---|---|---|
| Q1 | Does a higher budget lead to greater box office revenue? | Budget vs Revenue |
| Q2 | Which movie genres generate the highest revenue? | Revenue & Profit by Genre |
| Q3 | Is there a relationship between audience ratings and commercial success? | IMDb / Audience Score vs Revenue & ROI |
| Q4 | Which directors or actors consistently deliver successful movies? | Actor & Director Performance |

![Business Questions](Business-Questions)

---

## Q1 — Does a higher budget lead to greater box office revenue?

![Q1 Budget vs Revenue](Business-Questions/Q1%20Budget%20vs%20Revenue.png)

**Chart:** Budget (Million) on the X-axis, Revenue (Million) on the Y-axis — every point is one movie.

**Correlation (Python):** r = **0.614** — a moderate-to-strong positive relationship.

**What the shape tells you, beyond the correlation number:**
- There's a visible diagonal "ceiling" — very few movies exceed roughly 10× their budget in revenue. This isn't random; it represents a practical maximum return most films can realistically achieve.
- The spread *below* that ceiling is wide. At any given budget level (e.g. ~₹150M), revenue outcomes range enormously — from near-zero to several times the budget.

**Finding:** Higher-budget movies generally tend to generate higher revenue, showing a positive relationship between budget and box office revenue. **However, budget alone does not guarantee commercial success** — the wide spread of outcomes at every budget level means a large budget increases *potential* upside without removing downside risk.

---

## Q2 — Which movie genres generate the highest revenue?

![Q2 Revenue by Genre](Business-Questions/Q2%20Rev%20vs%20Genre.png)

![Q2 Profit by Genre](Business-Questions/Q2.1%20Profit%20vs%20Genre.png)

**Revenue by genre (highest to lowest):** Sci-Fi (575K) → Fantasy (555K) → Adventure (534K) → Action (486K) → Animation (424K) → Thriller (217K) → Comedy (187K) → Crime (186K) → Romance (167K) → Drama (163K)

**Profit by genre (highest to lowest):** Sci-Fi (271K) → Fantasy (264K) → Adventure (244K) → Action (229K) → Animation (200K) → Thriller (102K) → Comedy (88K) → Crime (85K) → Drama (80K) → Romance (78K)

**Finding:** **Sci-Fi generates the highest revenue, followed by Fantasy and Adventure**, making them the strongest revenue-generating genres in the analysis. The revenue and profit rankings are nearly identical across the top 8 genres — the only shift happens at the very bottom, where Drama and Romance swap positions (Romance leads on revenue, but Drama edges ahead on profit). This suggests genre strength is consistent whether you're optimizing for top-line revenue or bottom-line profit, with only a minor exception at the lower end.

---

## Q3 — Is there a relationship between audience ratings and commercial success?

### IMDb Rating vs ROI

![Q3 IMDb Rating vs ROI](Business-Questions/Q3%20imdb%20rating%20vs%20ROI.png)

**Correlation (Python):** r = **0.244** — a weak-to-moderate positive relationship.

As the project's own analysis notes: *low-rated movies (2–4) cluster tightly near zero or slightly negative ROI — a bad rating almost guarantees mediocre-to-poor financial performance. But once a movie crosses roughly a 5 rating, ROI outcomes become highly unpredictable — some highly-rated movies still lose money, while others achieve very high returns.* A good rating does not guarantee commercial success, but a bad rating almost guarantees a movie won't be a big financial hit.

### Audience Score vs Revenue

![Q3.1 Audience Score vs Revenue](Business-Questions/Q3.1%20Audience%20Score%20vs%20Revenue.png)

Higher audience scores are associated with a general upward trend in revenue — but the spread at every score level is wide, meaning strong audience reception does not reliably translate into high revenue on its own.

### Audience Score vs ROI

![Q3.2 Audience Score vs ROI](Business-Questions/Q3.2%20Audience%20Score%20vs%20ROI.png)

A similar pattern holds for ROI — a positive association exists, but with substantial scatter at every audience score level.

**Finding:** Higher audience scores generally show better revenue and ROI, while IMDb ratings also show a positive association with ROI. **However, the wide spread of points across all three charts indicates that ratings alone do not determine commercial success** — audience reception is a useful supporting signal, not an independent predictor.

---

## Q4 — Which directors or actors consistently deliver successful movies?

![Q4 Director Performance](Business-Questions/Q4%20Director%20Performance.png)

![Q4.1 Actor Performance](Business-Questions/Q4.1%20ActorPerformance.png.png)

This question is answered using **capped revenue** (see the Revenue Capping section above) combined with **standard deviation** — because "high performer" and "consistent performer" are two different things, and conflating them gives a misleading answer.

### Director Findings

| Director | Total Movies | SD | Avg Capped Revenue (M) | Avg Revenue (uncapped, M) |
|---|---|---|---|---|
| Sofia Coppola | 10,037 | 107.62 | 106.48 | 131.82 |
| Denis Villeneuve | 9,909 | 108.11 | 107.66 | 130.64 |
| Greta Gerwig | 10,096 | 109.58 | 108.06 | 131.68 |
| Quentin Tarantino | 10,053 | 110.54 | 109.03 | 131.65 |
| Martin Scorsese | 9,956 | 111.40 | 108.80 | 134.15 |
| James Cameron | 9,939 | 111.91 | 110.21 | 134.89 |
| Bong Joon-ho | 9,899 | 112.10 | 110.42 | 135.35 |
| Christopher Nolan | 10,066 | 112.91 | 110.08 | 133.09 |
| Steven Spielberg | 10,053 | 113.96 | 110.94 | 132.81 |
| **Patty Jenkins** | 9,992 | 115.16 | **113.07** | 137.09 |

*(sorted by SD, lowest first — i.e., most consistent first)*

**Patty Jenkins stands out among directors for strong overall commercial performance** — she has the highest average capped revenue (113.07M) of any director in the dataset.

### Actor Findings

| Actor | Total Movies | SD | Avg Capped Revenue (M) |
|---|---|---|---|
| Brad Pitt | 8,274 | 109.33 | 106.80 |
| Zendaya | 8,306 | 110.07 | 108.70 |
| Scarlett Johansson | 8,436 | 110.21 | 109.48 |
| Robert Downey Jr. | 8,355 | 110.91 | 108.76 |
| Timothee Chalamet | 8,382 | 111.25 | 109.51 |
| Christian Bale | 8,364 | 111.28 | 108.89 |
| Leonardo DiCaprio | 8,479 | 111.47 | 109.31 |
| Meryl Streep | 8,425 | 111.82 | 109.58 |
| Ryan Gosling | 8,241 | 112.20 | 110.93 |
| Jennifer Lawrence | 8,134 | 112.43 | 110.80 |
| Tom Hanks | 8,446 | 112.49 | 110.32 |
| Emma Stone | 8,158 | 112.88 | 110.64 |

*(sorted by SD, lowest first)*

**Among actors, Emma Stone, Ryan Gosling and Timothee Chalamet show strong performance across revenue, profit and ROI** — their strong results across multiple metrics indicate consistent contribution to movie success.

### The Consistency Angle

Looking at this same data through a *consistency* lens (lowest standard deviation = most stable performance), **Sofia Coppola and Brad Pitt stand out** — they post the lowest SD in their respective tables, meaning their financial performance varies the least from film to film. This doesn't mean they're the highest earners — Patty Jenkins and the top actor group lead on raw average capped revenue — but it means their output is the most *predictable*, which carries its own business value.

### Actor–Director Pairs

The dashboard also examines specific director–actor collaborations. The most consistent pairing found is **Jennifer Lawrence + Denis Villeneuve** (SD = 103.65) — the lowest standard deviation of any director–actor combination in the dataset, indicating this pairing produces the most stable, predictable financial outcomes when they work together.

### The Key Takeaway

> **High performer ≠ consistent performer.**
>
> A person can have a high average revenue but high variation (some huge hits, some misses) — or a slightly lower average revenue with much more stable, predictable performance. Patty Jenkins and Emma Stone lead on raw average capped revenue. Sofia Coppola and Brad Pitt lead on consistency. Both are valid, different answers to "who delivers success" depending on whether a studio is optimizing for upside potential or predictable, lower-risk returns.

**A note on future improvement:** a stronger future measure would define a clear revenue-success threshold and calculate the percentage of each director's or actor's films that cross that threshold — this would give a "hit rate" metric that's more directly interpretable than standard deviation alone.

---

## 📐 Understanding Standard Deviation (In Simple Terms)

Standard deviation measures how spread out a set of numbers is from their average.

**If revenue values are:** `90, 95, 100, 98, 97`
These are close together → **low standard deviation** → stable, predictable performance.

**If revenue values are:** `20, 250, 40, 300, 50`
These are far apart → **high standard deviation** → less consistent, less predictable performance.

Applied to Q4: a director whose films all earn roughly similar revenue has a *low* SD — you know roughly what to expect from their next film. A director with one massive blockbuster and several modest performers has a *high* SD — their average looks good, but any individual film is a bigger gamble.

---

## 📊 Power BI Dashboard

**Why Power BI:** the cleaned, capped dataset needed to support interactive, filterable exploration across four very different business questions — Power BI's data modelling, DAX measures, and slicer/toggle interactivity made this possible in a single connected report rather than four separate static analyses.

**Pages:**

| Page | Purpose |
|---|---|
| **Home** | Entry point with headline KPIs and navigation to all analysis pages |
| **01 Movie Overview** | High-level portfolio snapshot — revenue/profit trends by year, genre performance |
| **02 Financial Performance** | Budget efficiency, revenue generation, and profitability (ROI, budget-vs-revenue scatter) |
| **03 Audience Insight** | How audience reception and ratings relate to commercial performance |
| **04 Crew Success** | Director and actor performance — toggleable between Director/Actor and six different metrics |
| **05 Business Questions** | The four core findings, summarized in plain business language |

**What was built:**
- **Data modelling:** the cleaned dataset (including the `revenue%20capped` column) loaded and modelled for cross-filtering across all pages
- **Power Query:** data import and shaping from the cleaned CSV
- **DAX:** measures for Total Revenue, Total Profit, Profit %, Avg ROI, Avg IMDb Rating, Avg Top 100 Probability, and the Director/Actor toggle logic on the Crew Success page
- **KPI cards:** headline metrics on every page for at-a-glance context
- **Interactive charts:** scatter plots, bar charts, and a year-over-year trend line, all filterable

📄 [Power BI PDF Export](Power-BI/Global%20Movie%20Dataset%20Analysis.pdf) · 📊 [Power BI PBIX File](Power-BI/Global%20Movie%20Dataset%20Analysis.pbix) · 📁 [Power-BI README](Power-BI/README.md)

---

## 🐍 Python Analysis

**Why Python:** before any dashboard could be trusted, the underlying data needed to be understood — its structure, its distributions, and its statistical relationships. Python (pandas, seaborn, matplotlib) was used for this exploratory and preparatory work.

**What was done:**
- Data quality verification (missing values, structural integrity)
- Derived column creation (`profit`, `roi`)
- Correlation analysis for Q1 (budget–revenue) and Q3 (IMDb rating–ROI)
- Outlier detection and IQR-based revenue capping, grouped by director, to support the Q4 crew analysis
- Distribution visualization (KDE plots) comparing revenue before and after capping

📁 [Python Notebook](Python-File/Global-Movie-Success-Analysis.ipynb) · 📁 [Python-File README](Python-File/README.md)

---

## 🔎 Key Insights & Findings

### 💰 Financial
- Budget and revenue show a moderate-to-strong positive correlation (r = 0.614) — but a hard ceiling exists near 10× budget-to-revenue, and outcomes below that ceiling vary enormously at every budget level.
- Total portfolio: 13.33M revenue, 4.83M budget, 6.21M profit, 46.56% profit margin, 176.87% average ROI.

### 🎬 Genre
- Sci-Fi leads on both revenue (575K) and profit (271K), followed consistently by Fantasy and Adventure.
- Genre rankings are stable between revenue and profit views, with only Romance/Drama swapping at the bottom of the list.

### ⭐ Audience
- Audience score and IMDb rating both show positive associations with revenue and ROI (r = 0.244 for IMDb–ROI specifically) — real but weak relationships.
- A poor rating almost guarantees weak financial performance; a good rating does not guarantee strong performance — the risk is asymmetric.

### 🎭 Crew
- Patty Jenkins (director) and the actor group of Emma Stone, Ryan Gosling, and Timothee Chalamet post the strongest average capped revenue.
- Sofia Coppola (director) and Brad Pitt (actor) are the most *consistent* performers, with the lowest standard deviation in their respective groups.
- The most consistent director-actor pairing is Jennifer Lawrence + Denis Villeneuve.

---

## 💡 Business Recommendations

### 01 — Budget Strategy
Do not rely on budget alone when approving projects. A larger budget raises the *ceiling* on potential revenue but does not reduce downside risk — pair budget decisions with genre and talent-consistency data rather than treating spend as a success guarantee.

### 02 — Genre Strategy
Prioritize Sci-Fi, Fantasy, and Adventure projects where the goal is maximizing revenue and profit, while still weighing each genre's typical production cost — since profit and revenue rankings track closely, genre selection is a relatively low-risk lever compared to budget alone.

### 03 — Audience Strategy
Use audience and critic reception as a supporting signal in greenlighting and marketing decisions, not a standalone success predictor. The data shows a poor rating is a stronger warning sign than a good rating is a guarantee.

### 04 — Talent Strategy
Evaluate directors and actors using both average performance *and* consistency (standard deviation). A studio seeking a high-upside bet should look at raw average capped revenue leaders (Patty Jenkins, Emma Stone); a studio seeking predictable, lower-risk returns should look at the most consistent performers (Sofia Coppola, Brad Pitt).

### 05 — Risk Management
Do not select talent based on one exceptionally successful movie. The capping methodology exists precisely because a single blockbuster can make an otherwise inconsistent performer look like a safe bet — always check the standard deviation alongside the average before committing to a director or actor pairing.

---

## 🎯 Problem Solved

| Dimension | What We Learned |
|---|---|
| **Financial** | Budget and revenue are positively correlated (r = 0.614), but budget alone doesn't guarantee success — outcomes vary widely at every spend level. |
| **Genre** | Sci-Fi, Fantasy, and Adventure are the strongest revenue and profit generators, with consistent rankings across both metrics. |
| **Audience** | Ratings and audience scores are positively associated with commercial performance (weak-to-moderate strength) but cannot independently predict it. |
| **Crew** | High average performance (Patty Jenkins, Emma Stone) and high consistency (Sofia Coppola, Brad Pitt) are different, both valuable signals — the right talent choice depends on whether a studio wants upside or predictability. |

---

## 🏁 Final Conclusion

Movie commercial success is **multi-factor** — no single variable in this dataset determines whether a film succeeds.

Budget matters, but does not guarantee success: it raises the ceiling on potential revenue without controlling the floor. Genre can meaningfully influence financial performance, with Sci-Fi, Fantasy, and Adventure consistently outperforming other categories on both revenue and profit. Audience reception provides a genuinely useful signal — particularly as a downside warning, since poor ratings are strongly associated with weak returns — but strong ratings alone don't guarantee a hit. Crew performance needs to be evaluated using multiple metrics, because average performance and consistency of performance are genuinely different things, and conflating them risks over-trusting a track record built on a single outlier success.

The strongest decision-making approach for a studio combines all of these signals together:

**Budget + Genre + Audience + Talent + Profit + ROI + Consistency**

No single lens tells the full story — but together, they turn 100,000 rows of raw movie data into a defensible, evidence-based view of what actually drives commercial success.

---

## 📁 Repository Structure

```
03%20Global-Movie-Success-Analysis/
├── Data/
│   ├── Raw-Data/
│   │   ├── README.md
│   │   └── global%20movies%20dataset%201950%202026.csv
│   ├── Cleaned-Data/
│   │   ├── README.md
│   │   └── Python%20Cleaned%20Data.csv
│   └── README.md
├── Python-File/
│   ├── README.md
│   └── Global-Movie-Success-Analysis.ipynb
├── Power-BI/
│   ├── README.md
│   ├── Global Movie Dataset Analysis.pbix
│   └── Global%20Movie%20Dataset%20Analysis.pdf
├── Business-Questions/
│   ├── README.md
│   ├── Q1%20Budget%20vs%20Revenue.png
│   ├── Q2%20Rev%20vs%20Genre.png
│   ├── Q2%201%20Profit%20vs%20Genre.png
│   ├── Q3%20imdb%20rating%20vs%20ROI.png
│   ├── Q3%201%20Audience%20Score%20vs%20Revenue.png
│   ├── Q3%202%20Audience%20Score%20vs%20ROI.png
│   ├── Q4%20Director%20Performance.png
│   └── Q4%201%20ActorPerformance%20png.png
├── Screenshots/
│   ├── README.md
│   ├── Home%201.png
│   ├── Movie%20Overview.png
│   ├── Financial%20%20Perf.png
│   ├── Audience%20Insight.png
│   ├── Crew%20Performance.png
│   ├── Business%20Questions.png
│   └── BQ4%20Detailed%20Ans.png
├── Presentation/
│   ├── README.md
│   └── Movie%20Analysis.pptx
└── README.md
```

---

## 📦 Project Deliverables

| Deliverable | Link |
|---|---|
| Raw Data | [Data/Raw-Data/](Data/Raw-Data/) |
| Cleaned Data | [Data/Cleaned-Data/](Data/Cleaned-Data/) |
| Python Notebook | [Python-File/Global-Movie-Success-Analysis.ipynb](Python-File/Global-Movie-Success-Analysis.ipynb) |
| Power BI PBIX | [Power-BI/Global%20Movie%20Dataset%20Analysis.pbix](Power-BI/Global%20Movie%20Dataset%20Analysis.pbix) |
| Power BI PDF | [Power-BI/Global%20Movie%20Dataset%20Analysis.pdf](Power-BI/Global%20Movie%20Dataset%20Analysis.pdf) |
| Business Questions (Visuals) | [Business-Questions/](Business-Questions/) |
| Screenshots | [Screenshots/](Screenshots/) |
| Final Presentation | [Presentation/Movie%20Analysis.pptx](Presentation/Movie%20Analysis.pptx) |

---

## 🔗 Connect

- **GitHub:** [PiyushDave30](https://github.com/PiyushDave30)
---

*Team 3 — InsightNest · Keshav Baheti (Python & EDA) · Piyush Dave (Power BI & Dashboard) · Global Movies Dataset (Kaggle)*
