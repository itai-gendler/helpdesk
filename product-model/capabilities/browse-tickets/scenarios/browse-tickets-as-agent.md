---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent opens the ticket list, filtering and sorting it
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Subject
    - Status
    - Priority
    - Ticket type
    - Team
    - Customer
    - Assigned agents
    - First response due
    - Resolution due
    - SLA status
    - Rating
  contexts:
    main:
      place: helpdesk-web::agent-portal::tickets
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Browse tickets as an agent

## Trigger

An Agent opens the ticket list.

## Outcome

The Agent sees the Tickets they may see, with status, priority, team, assignees and SLA targets.

## Decision points

### Team restriction

Is Restrict tickets by team on?

- Off → every ticket is listed
- On → only the agent's teams' tickets, tickets assigned to them, tickets they raised and, if allowed, tickets without a team are listed
