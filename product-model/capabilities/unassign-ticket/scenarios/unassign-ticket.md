---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent removes an assignee from the Ticket
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Assigned agents
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product cancels that Agent's assignment on the Ticket
  kind: product
  actor: agent
  entities:
  - entity: ticket
    effect: changes
    facts:
    - Assigned agents
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/api/doc.py
---

# Remove an assignee

## Trigger

An Agent takes an Agent off a Ticket.

## Outcome

The Agent is no longer assigned.
