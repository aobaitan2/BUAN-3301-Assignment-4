# Business case: a "Quick Win"

**Domain:** Customer Service
**Goal:** Cost Reduction

## The problem

Support agents spend a large share of their time reading, categorizing, and routing tickets before they can start solving them. Slow triage delays responses, risks missing SLAs, and increases cost per ticket.

## The solution

An AI agent performs the first pass on every ticket: classify, prioritize, route, and draft a reply where safe. A human reviews and approves before anything goes out.

## Hype vs. Value placement

| Axis | Rating | Why |
|---|---|---|
| Business impact | High | Triage and first drafts are repetitive, high-volume work, and faster handling lowers cost per ticket |
| Technical feasibility | High | Uses off-the-shelf LLMs plus existing ticket history and help docs, no custom training, pilot in weeks |
| Risk | Low | A human approves every reply |

## Why not the other quadrants

- **Not a Moonshot:** A fully autonomous agent that resolves tickets and issues refunds with no human review has high impact but high risk, heavy integration work, and trust problems.
- **Not a Money Pit:** Training a custom in-house language model, or adding AI features customers did not ask for, costs a lot for little return.

## Success metrics

Average handle time, first-response time, tickets per agent per day, and agent acceptance rate of suggested drafts. See [tokenomics_and_roi.md](tokenomics_and_roi.md) for the KPI targets.
