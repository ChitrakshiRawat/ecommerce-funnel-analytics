[README.md](https://github.com/user-attachments/files/31115410/README.md)
# E-commerce Analytics: Revenue, Funnel & A/B Testing

A data-driven e-commerce analysis uncovering key profit drivers, conversion bottlenecks, and marketing channel performance, with A/B testing results validated for statistical significance to support confident, evidence-based business decisions.

Built using the Maven Fuzzy Factory dataset, a simulated e-commerce business selling plush toys online.

---

## Project Overview

This project answers a set of core business questions by cleaning, merging, and analyzing six raw data tables, then building out profitability, marketing, and conversion analyses, culminating in a full purchase funnel breakdown and statistically rigorous A/B testing of two live experiments (a billing page redesign and five landing page variants).

**Business questions answered:**
- What is our total profit, and how much are we losing to refunds?
- Which products sell best, and worst?
- How have sessions, orders, and conversion rate trended over time?
- Which marketing channels drive the most, and best-converting, traffic?
- What is revenue per order and per session, and how has it evolved?
- Where in the purchase journey do customers drop off?
- Did our billing page redesign actually improve conversion?
- Which landing page variant performs best, and is the difference real or just noise?

---

## Data

Six raw CSV files, sourced from the Maven Fuzzy Factory practice dataset:

| File | Description |
|---|---|
| `orders.csv` | One row per completed order |
| `order_items.csv` | Line-item level detail per order (price, cost) |
| `order_item_refunds.csv` | Refund records |
| `products.csv` | Product catalog |
| `website_sessions.csv` | Session-level traffic data (channel, campaign, device) |
| `website_pageviews.csv` | Page-level view events per session |

---

## Tools & Methods

- **Microsoft Excel** - Power Query (data cleaning, merging/joins, session-level aggregation), PivotTables, and formula-driven statistical testing
- **Statistical testing** - two-proportion Z-tests, built from first principles (pooled proportion, standard error, Z-score, p-value), to validate A/B test results rather than relying on raw percentage comparisons

---

## Key Analyses

1. **Profitability** - total profit, total refunds, net profit
2. **Product Performance** - top and least selling items, most-refunded product
3. **Traffic & Conversion Trends** - monthly sessions, orders, and conversion rate over time
4. **Marketing Channel Performance** - session volume and conversion rate by channel (gsearch, bsearch, socialbook, direct/untracked)
5. **Revenue Metrics** - revenue per order and per session, trended monthly
6. **Funnel Analysis** - session-level drop-off across the full purchase journey (Landing to Product to Cart to Shipping to Billing to Purchase)
7. **A/B Testing** - statistical significance testing on:
   - Billing page redesign (`/billing` vs `/billing-2`)
   - Five landing page variants vs. the `/home` baseline

---

## Key Findings

### Profitability
- Gross profit: **$2,541,065.50**
- Total refunds: **$85,338.69**
- Net profit (after refunds): **$2,455,726.81**

### Revenue
- Total revenue: **$4,003,415.03** across 55,449 orders and 496,007 sessions
- Revenue per order: **~$72.20** (ranged from ~$70 to ~$74 month over month)
- Revenue per session: **~$8.07** (ranged from ~$7.10 to ~$9.57 month over month)

### Marketing Channels
- **gsearch** is the dominant channel by both traffic volume (330,969 sessions) and revenue ($2,611,062.21)
- **bsearch** contributes meaningfully but at a smaller scale (65,916 sessions, $543,686.64 revenue)
- Untracked/direct traffic (NULL source) still accounts for a notable 88,065 sessions and $793,060.29 in revenue

### Funnel Analysis
- Overall funnel conversion: **~6.8%** of sessions result in a completed purchase (32,313 of 472,871 sessions)
- Stage-by-stage conversion:
  - Home to Product: 55%
  - Product to Cart: **36%** (the single biggest drop-off in the funnel)
  - Cart to Shipping: 68%
  - Shipping to Billing: 81%
  - Billing to Purchase: 62%
- The largest opportunity for improvement sits between the product page and the cart, where roughly two-thirds of visitors who view a product never add it to their cart.

### A/B Test: Billing Page Redesign
- `/billing` (v1): 3,617 sessions, 1,620 purchases -> 44.79% conversion
- `/billing-2` (v2): 48,441 sessions, 30,693 purchases -> 63.36% conversion
- Z = -75.31, p < 0.001
- Result: statistically significant. `/billing-2` outperforms `/billing` by a wide margin.

### A/B Test: Landing Page Variants (vs. `/home` baseline, 7.06% conversion)

| Page | Sessions | Conversion Rate | Z-score | Result vs. Home |
|---|---|---|---|---|
| Lander-1 | 47,574 | 4.53% | -34.73 | Significantly worse |
| Lander-2 | 131,170 | 7.72% | -46.86 | Significantly better |
| Lander-3 | 79,000 | 3.39% | -32.64 | Significantly worse |
| Lander-4 | 9,385 | 7.54% | -27.48 | Significantly better |
| Lander-5 | 68,166 | 10.17% | -79.54 | Significantly better (best performer) |

All five differences were statistically significant at p < 0.001. Lander-5 is the strongest performing landing page and a candidate for increased traffic allocation; Lander-1 and Lander-3 significantly underperform the home page baseline and are candidates for redesign or retirement.

---

## Files

- `Maven analysis.xlsx` - full analysis workbook (all PivotTables, formulas, and charts)
- Raw CSVs - source data
- `maven_fuzzy_factory_data_dictionary.csv` - column reference

---

## Possible Next Steps

- Interactive Tableau dashboard built on the same dataset
- Chi-square test across all landing page variants simultaneously, rather than pairwise comparisons against home

---

Analysis conducted in Excel/Power Query. Statistical tests are two-tailed, alpha = 0.05.
