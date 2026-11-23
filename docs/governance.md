# Runtime liability and enterprise governance

## Human-in-the-loop and corporate liability

In *Moffatt v. Air Canada* (2024), a tribunal held an airline responsible for incorrect information its website chatbot gave a customer, rejecting the argument that the chatbot was a separate entity. The lesson is that a company owns what its AI says.

The human-in-the-loop (HITL) gate prevents this exposure:

- The agent only creates **drafts**. A trained employee approves every outgoing reply.
- Refunds over $500 require manager approval.
- P1 and security tickets are never auto-drafted.
- Claims of authority, prompt injections, etc. inside of a ticket cannot skip the gate.

A wrong statement has to reach the customer to create liability for negligent misrepresentation, and the gate stops it before it does.

## Enterprise IT governance in production

### Closed-tenant licensing

The tool would run under an enterprise license where ticket data is contractually excluded from model training and stays inside the company's environment. This prevents Shadow AI leaks like the 2023 Samsung incident, where employees pasted confidential source code into a public chatbot.

### Non-Human Identity (NHI)

The agent runs as a service account, not under a person's login, with least-privilege access:

- Read tickets
- Write the triage tracker
- Nothing else

### Zero Trust micro-segmentation

- Short-lived credentials that expire and rotate
- No network path from the agent to payment or billing systems
- Every action logged for audit


