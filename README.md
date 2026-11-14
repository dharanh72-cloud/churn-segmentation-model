# Customer Segmentation & Rule-Based Churn-Risk Score

Explainable churn-risk scoring and customer segmentation on a **synthetic** dataset of 15 customers. Findings are illustrative, not real-world insights.

## Contents
| File | Purpose |
|---|---|
| `churn_segmentation.ipynb` | Full notebook: feature choice, score, edge-case tests, sensitivity check, segments, charts |
| `segment_table.csv` | Four segments with counts, churn, tenure, tickets, charges, revenue |
| `scored_customers.csv` | Every customer with risk score, tier and segment |
| `recommendation_memo.md` | Plain-language memo with one retention action per segment |
| `customer_churn_sample.csv` | Raw input data |

## The score (0-100, additive)
| Rule | Points |
|---|---|
| Contract: Month-to-Month / One Year / Two Year | 40 / 15 / 0 |
| Tenure: 12 months or less / 13-24 / over 24 | 30 / 15 / 0 |
| Support tickets: 3 or more / 1-2 / none | 30 / 10 / 0 |

High risk is 60 or more, Medium 30-59, Low under 30. Churn is never an input.

## Segments
| Segment | Customers | Action (summary) |
|---|---|---|
| A. High risk, higher value | 2 | Personal outreach plus 12-month contract offer |
| B. High risk, standard value | 5 | Onboarding and support follow-up in first 90 days |
| C. Watch list | 4 | Renewal reminder 60 days before contract end |
| D. Loyal core | 4 | No discounts; light nurture |

## Validation
- 8 boundary and edge-case tests pass; invalid inputs (unknown contract, negative or missing values) are rejected with errors.
- Tiers are stable across 12 cutoff variations (at most 1 customer moves).
- All 7 High-risk customers churned and none of the other 8 did. **This is not proof the model works**: 15 rows, rules chosen after exploring the same data, synthetic data.

## Limitations
Tiny sample, overlapping features, synthetic data, and no hold-out set. Recommendations are hypotheses to A/B test.

## How to run
Place `customer_churn_sample.csv` next to the notebook, install `pandas`, `numpy` and `matplotlib`, and run all cells.
