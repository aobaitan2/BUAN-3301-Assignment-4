# Synthetic dataset

No real customer data was used. Regulations such as HIPAA, GDPR, and SOC 2 prohibit testing software on real customer data, so `synthetic_support_tickets.csv` acts as the "crash test dummy."

It contains 41 fabricated tickets. Each row has the inputs the agent sees plus the correct answer, so the agent's output can be checked.

## Columns

| Column | Meaning |
|---|---|
| `ticket_id` | Unique ID |
| `customer_tier` | Free, Standard, Premium, or Enterprise |
| `channel` | Email, Chat, Phone, or Web Form |
| `category` | Billing, Refund, Shipping, Technical, Account Access, Security, or General |
| `subject`, `body` | Ticket text |
| `sentiment_score` | -1 (very negative) to 1 (very positive) |
| `prior_tickets_30d` | Tickets from the same customer in the last 30 days |
| `order_value_usd`, `refund_requested_usd` | Dollar amounts |
| `hours_open`, `sla_hours`, `sla_pct_used` | Time open, SLA for the tier, and percent used |
| `classifier_confidence` | 0 to 1 |
| `expected_priority`, `expected_queue`, `expected_auto_draft`, `escalation_flags` | The answer key |
| `edge_case_note` | Why the row exists |

## Business rules

| Rule | Threshold | Effect |
|---|---|---|
| SLA by tier | Enterprise 4h, Premium 8h, Standard 24h, Free 48h | Sets deadline |
| Base priority | Security P1, Technical P2, Billing/Refund/Account Access/Shipping P3, General P4 | Starting point |
| SLA nearly used | 80% or more of SLA elapsed | Priority up one level |
| Negative sentiment | Score of -0.60 or lower | Priority up one level |
| Enterprise tier | Always | Priority up one level |
| Security keywords | Unauthorized charge, hacked, phishing | Always P1, Security Queue |
| Large refund | Over $500 (strictly greater) | Billing Tier 2 (manager approval) |
| Repeat contact | 3 or more tickets in 30 days | Senior Agent |
| Auto-draft allowed | Confidence 0.85 or higher, P3 or P4, not security, refund $500 or less, fewer than 3 prior tickets | Otherwise human first |

Priority bumps never go above P1. Routing is checked in this order: security, large refund, repeat contact, then category.

## Edge cases included

- Exact boundaries: refund of $500.00 vs. $500.01, sentiment of exactly -0.60, exactly 3 prior tickets, exactly 80% of SLA (for example 19.2 of 24 hours), confidence of 0.85 vs. 0.849
- Sarcasm, where the sentiment score contradicts the text
- A non-English ticket
- An empty ticket
- Duplicate submissions
- A ticket mixing billing and security signals
- Stacked rules: Enterprise tier plus a large refund plus repeat contact

Red-team test files are in [redteam/](redteam/).
