# Retention Recommendation Memo

**To:** Customer Success / Retention team  **Re:** Where to focus retention effort  
**Data:** synthetic sample of 15 customers. Treat every recommendation below as a hypothesis to test, not a proven result.

## Summary
Seven of 15 customers (46.7%) churned. A simple, transparent risk score (contract type, tenure, support tickets) splits customers into four segments. The customers who left were all Month-to-Month, in their first 14 months, with 3 or more support tickets. The customers who generate almost half of monthly revenue (47%) sit in the lowest-risk segment.

## How the risk score works
Points out of 100: contract (Month-to-Month 40, One Year 15, Two Year 0) + tenure (12 months or less 30, 13-24 months 15, over 24 months 0) + support tickets (3 or more 30, 1-2 10, none 0). High risk is 60 or more, Medium 30-59, Low under 30. The outcome (churn) was never used to calculate the score.

## Segments and actions
| Segment | Customers | Monthly revenue | Recommended action |
|---|---|---|---|
| **A. High risk, higher value** (Pro plan, Month-to-Month) | 2 | 159.98 | **Personal outreach within a week**, with an offer to move to a 12-month contract at a small loyalty discount. Highest value per save. |
| **B. High risk, standard value** (Basic plan, Month-to-Month) | 5 | 249.95 | **Proactive onboarding and support follow-up in the first 90 days.** Fix repeat tickets before offering discounts. Average 4.6 tickets and 5.4 months tenure suggest a service problem, not a price problem. |
| **C. Watch list** (One Year contracts) | 4 | 259.96 | **Renewal reminder with a loyalty offer 60 days before the contract ends.** Not at risk today, but the contract end is the exit point. |
| **D. Loyal core** (Enterprise, Two Year) | 4 | 599.96 | **No discounts.** Light-touch nurture (referral invite, product updates). Protect this group rather than spend retention budget on it. |

Segments A and D are the high-value groups: A is where a save is worth the most per customer among those at risk, and D is where the most revenue sits.

## Why not trust this too much
- **Tiny sample:** 15 customers. The score separates churners perfectly (all 7 High-risk customers churned, none of the other 8), but I chose the rules after looking at this same data, so this proves nothing about how it would perform on new customers.
- **Overlapping features:** contract, tenure and plan move together (every Enterprise customer is on a Two Year contract), so the data cannot say which one causes churn.
- **Synthetic data:** patterns are illustrative only.
- **What I tested:** boundary values, invalid inputs (rejected with clear errors), and sensitivity to the cutoffs (1 of 12 tested cutoff combinations moves a single customer). This shows the score is stable and well-behaved, not that it is accurate.

## Next step
Run each action on a small group with a comparison group left untouched, for 90 days, then compare churn. Re-fit or re-check the score on a real hold-out period before relying on it.
