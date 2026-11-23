# Tokenomics and 1-year financial model

## Model routing

Token consumption is treated like a corporate utility bill: use the cheapest model that can do each job.

| Task | Model tier | Share of tickets |
|---|---|---|
| Classification, priority, routing, flag checks, routine P3 and P4 drafts | Cheap, fast model (Haiku or DeepSeek class) | About 80% |
| Ambiguous or low-confidence tickets, sarcasm, mixed security and billing, P1 and Enterprise drafts | Frontier model (Opus or GPT-5 class) | About 20% |

**Context window limits:** send only the current ticket, the rules, and the customer record. Do not resend ticket history or the full CSV. Cap the prompt at about 1,500 tokens for routine tickets and about 3,000 for complex ones.

**Why routing matters:** sending all 180,000 tickets a year to a frontier model would cost about $5,400 in tokens, compared with about $1,500 with routing (using the illustrative prices below).

## Assumptions

Mid-sized enterprise: 15,000 tickets per month, or 180,000 per year.

| Item | Assumption |
|---|---|
| Time saved per ticket | 2.5 minutes (triage plus first draft) |
| Agent fully loaded cost | $32/hour |
| Adoption factor | 70% (agents accept or lightly edit drafts) |
| SLA-penalty avoidance | $24,000/year |
| Cheap model tokens | About 1,500 in / 300 out per ticket, at $1 in / $5 out per million tokens (illustrative) |
| Frontier model tokens | About 3,000 in / 600 out per ticket, at $5 in / $25 out per million tokens (illustrative) |
| API token cost | About $1,500 computed, $2,000 with a 30% buffer |
| Cloud hosting | $300/month ($3,600/year) |
| Setup labor | 160 hours at $75 ($12,000) |
| Closed-tenant licenses | $25/seat/month, 30 seats ($9,000/year) |
| Governance and monitoring | 10 hours/month at $75 ($9,000/year) |


## Calculation

**Total value generated**

- Labor saved: 180,000 tickets x 2.5 min = 7,500 hours. At 70% adoption: 5,250 hours x $32 = **$168,000**
- SLA-penalty avoidance: **$24,000**
- **Total value = $192,000**

**Total investment**

| Item | Cost |
|---|---|
| Setup labor | $12,000 |
| Cloud hosting | $3,600 |
| API tokens | $2,000 |
| Closed-tenant licenses | $9,000 |
| Governance and monitoring | $9,000 |
| **Total** | **$35,600** |

**ROI**

```
ROI (%) = (Total Value - Total Investment) / Total Investment x 100
        = (192,000 - 35,600) / 35,600 x 100
        = about 439%
```

**Payback period**

```
Payback (months) = Total Investment / Monthly Value
                 = 35,600 / (192,000 / 12)
                 = about 2.2 months
```

This is conservative: it treats all investment as upfront and assumes full benefit from month one. Real ramp-up would push payback out slightly.

## Success KPIs

| Type | Metric | Target |
|---|---|---|
| **Hard** | Average handle time | 8.0 to 5.5 minutes |
| **Hard** | Tickets answered within SLA | 95% |
| **Soft** | Agent burnout from repetitive work | Improvement on quarterly survey |
| **Soft** | Agent trust and confidence in the tool | Improvement on quarterly survey (low trust means agents rewrite every draft and erase the savings) |
