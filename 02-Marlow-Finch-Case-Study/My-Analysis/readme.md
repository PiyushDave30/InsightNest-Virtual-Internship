# My Analysis

## What's in this folder
Two documents that cover my full process on the Marlow & Finch case study — from first reading the brief to answering the guiding questions. Both are based only on the aggregate numbers in [Brief](https://github.com/PiyushDave30/InsightNest-Virtual-Internship/tree/main/02-Marlow-Finch-Case-Study/Brief) no raw transaction-level data has been shared yet.

---

## [Marlow_Finch_Initial_Understanding_and_Approach](Marlow_Finch_Initial_Understanding_and_Approach.docx)

My first pass on the brief, written before doing any analysis — this is where I broke the problem down and planned how to approach it.

**What it covers:**
- The problem statement rewritten in my own words, to make sure I actually understood it before starting.
- A recap of the company overview and org structure (channels, headcount by function, category mix).
- Key KPIs pulled from the brief, listed out in one place for quick reference.
- A section-by-section breakdown of all six flagged issues — for each one, I listed:
  - The relevant numbers from the brief
  - The specific questions I'd want answered (e.g. under Décor: *why is revenue continuously dropping, is it due to old inventory, are we pricing it wrong*)
  - An initial "Suggestion" on which direction to investigate first
- The final list of guiding questions and data sources, restated as a checklist to work through.

**Why this exists:** before jumping into conclusions, I wanted to lay out everything I was uncertain about and what I'd need to check — this is the planning stage, not the answer stage.

---

## [Marlow_Finch_Findings_and_Recommendations](Marlow_Finch_Findings_and_Recommendations.docx)

My answers to the guiding questions, built entirely from the numbers already available in the brief.

**What it covers:**
- A finding for each guiding question, for example:
  - Which channel is actually driving the revenue decline (by dollar impact, not just percentage)
  - Whether Retail's decline is mostly traffic, conversion, or ticket size
  - Whether DTC growth is realistically big enough to be cannibalizing Retail
  - Whether margin erosion is coming from channel mix or from rising markdowns
  - Whether the inventory problem is overbuying overall or misallocation between categories
  - Why Décor specifically is underperforming compared to the other four categories
- A short "Suggestion" after each finding — what I'd check next, or what action it points toward.
- A **prioritized list of root causes**, ranked by how much impact each one likely has.
- **Recommendations split by team** — Merchandising & Buying, Store Operations, and Wholesale/Sales — so each team gets specific, actionable next steps rather than one generic list.
- A **"data still needed"** section listing exactly what raw data (account-level wholesale data, store-level stockout data, SKU-level markdown reason codes, etc.) would be required to confirm these findings properly.

**Why this exists:** this is the actual deliverable the brief asks for — root causes and recommendations — but built responsibly, i.e. clearly marked as directional since it's based on brief-level numbers and not yet validated against transaction data.

---

## Status
These findings are a first pass, not final. They're grounded in the aggregate figures from the brief and are meant to narrow down which hypotheses are worth pursuing further. Once raw POS, e-commerce, wholesale, and inventory data is shared, this analysis will be re-validated and expanded — likely with a Power BI dashboard to support the findings visually.
