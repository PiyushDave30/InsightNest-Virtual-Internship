# Marlow & Finch — Sales & Margin Diagnostic Case Study

## About
This is a practice client-diagnostic case study completed as part of my Data Analyst virtual internship at InsightNest. Marlow & Finch is a fictional omnichannel home & lifestyle products retailer — the company, figures, and data used here are constructed for training purposes and do not represent a real business.

The exercise simulates a real analyst engagement. A diagnostic brief describing the business problem was provided, and my task was to work through it the way an analyst would on an actual project — understand the brief, form hypotheses, ask the right questions, and answer the guiding questions using the data available, before eventually validating everything against raw data.

## Company Snapshot
Marlow & Finch is a Denver-based retailer selling home, kitchen, and lifestyle products through three channels: 42 company-owned retail stores, a DTC e-commerce site, and ~310 wholesale accounts. Products span five categories — Kitchen, Dining, Textiles, Décor, and Storage & Organization. The company is PE-backed since 2021, has ~1,150 employees, and has historically competed on quality and in-store experience rather than price.

## Problem Statement
Marlow & Finch is experiencing revenue decline and falling profitability at the same time. Revenue dropped year-over-year in every quarter of FY25, and gross margin fell from 52.4% to 44.9% (-7.5 points) over two years. DTC e-commerce is growing, but Retail Stores and Wholesale — the two biggest revenue channels — are both declining sharply. Leadership doesn't yet know whether this is mainly due to falling customer demand, poor inventory/merchandising decisions, or DTC growth cutting into Retail sales. The goal of this diagnostic is to identify which factors are actually responsible, quantify their impact, and prioritize where the business should intervene first.

## Folder Structure

```
02-Marlow-Finch-Case-Study/
├── README.md
├── brief/
│   ├── README.md
│   └── Marlow_Finch_Client_Diagnostic_Brief.pdf
└── my-analysis/
    ├── README.md
    ├── Marlow_Finch_Initial_Understanding_and_Approach.docx
    └── Marlow_Finch_Findings_and_Recommendations.docx
```

## Files

| File | Folder | What it is |
|---|---|---|
| [Marlow_Finch_Client_Diagnostic_Brief](Marlow_Finch_Client_Diagnostic_Brief.pdf) | [Brief]() | The diagnostic brief — company overview, 8-quarter revenue & margin data by channel, category/inventory numbers, and the six issues leadership flagged for investigation. |
| [Marlow_Finch_Initial_Understanding_and_Approach](Marlow_Finch_Initial_Understanding_and_Approach.docx) | [My-Analysis]() | My first pass on the brief — problem restated in my own words, and for each flagged issue, the questions I planned to investigate and my initial direction. |
| [Marlow_Finch_Findings_and_Recommendations](Marlow_Finch_Findings_and_Recommendations.docx) | [My-Analysis]() | My answers to the guiding questions based on the brief's numbers — findings, prioritized root causes, and recommendations split by team. |

## Approach
The brief raises six issues, each treated as a hypothesis to be tested rather than an established fact:

1. **Revenue decline** — which channel is really driving it, and is it traffic, conversion, or ticket size?
2. **Margin erosion** — is it channel mix, rising markdowns, or something else?
3. **Inventory imbalance** — overbuying overall, or buying the wrong categories?
4. **Store fleet underperformance** — which stores, and is there a common pattern (region/format)?
5. **Décor category weakness** — demand issue, product/assortment issue, or pricing issue?
6. **Wholesale decline** — a few large accounts leaving, or many small ones ordering less?

## Key Findings (Summary)
- **Retail** is the biggest dollar driver of the revenue decline (-$3.7M), bigger than Wholesale's loss in absolute terms even though Wholesale's percentage drop is steeper.
- Retail's decline is mainly **traffic-driven**, with a secondary drop in conversion rate suggesting an in-store execution factor as well.
- **DTC growth (+$1.6M) is too small to explain most of Retail's loss (-$3.7M)** — cannibalization is unlikely to be the primary cause.
- **Margin erosion looks driven by rising markdowns (23% → 31%)**, not by channel mix — the mix shift toward high-margin DTC should have helped margin, not hurt it.
- The inventory issue looks like **misallocation, not blanket overbuying** — Décor is overstocked and aging while Storage & Organization is stocking out despite strong sell-through.
- **Décor's 22% revenue share makes its weak performance disproportionately damaging** to company-wide numbers.

Full detail, numbers, and reasoning for each point are in `my-analysis/Marlow_Finch_Findings_and_Recommendations.docx`.

## Status
✅ Initial findings and recommendations complete, based on the aggregate numbers in the brief.
🔄 Not yet validated against raw transactional data (POS, e-commerce, wholesale, inventory) — that data hasn't been shared yet. Once it is, this analysis will be checked against it and a Power BI dashboard will be added.

## Disclaimer
All company names, figures, and data in this case study are fictional and were created only for internship training and analyst practice purposes.
