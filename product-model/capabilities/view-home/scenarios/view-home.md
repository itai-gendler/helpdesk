---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent opens Home and picks a period
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Subject
    - Status
    - Assigned agents
    - First response time
    - Resolution time
    - Rating
  contexts:
    main:
      place: helpdesk-web::agent-portal::home
references:
- kind: code
  role: implementation
  target: helpdesk/api/agent_home/agent_home.py
---

# View one's home

## Trigger

An Agent opens Home.

## Outcome

The Agent sees their own tickets and figures.

## Edge cases

- The agent may rearrange the home cards or reset them to the default layout.
