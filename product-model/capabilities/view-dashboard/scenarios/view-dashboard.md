---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent picks a period, and a manager also whose figures
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Status
    - Team
    - Ticket type
    - Priority
    - SLA status
    - Rating
    - Raised via portal
  contexts:
    main:
      place: helpdesk-web::agent-portal::dashboard
references:
- kind: code
  role: implementation
  target: helpdesk/api/dashboard.py
---

# View the dashboard

## Trigger

An Agent opens the Dashboard for a period.

## Outcome

The Agent sees ticket and SLA figures within what they may see.

## Decision points

### Whose figures

Is the viewer an Agent Manager?

- Yes → the whole organization, any team or any agent
- No → only the agent's own figures
