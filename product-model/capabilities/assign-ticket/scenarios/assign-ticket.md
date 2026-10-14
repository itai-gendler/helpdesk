---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent picks Agents, seeing each one's availability
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Assigned agents
    - Team
  - entity: agent
    effect: reads
    facts:
    - Agent name
    - Availability
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product assigns the chosen Agents to the Ticket
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
- text: The Product notifies and emails each newly assigned Agent
  kind: product
  actor: agent
  entities:
  - entity: agent
    effect: reads
    facts:
    - Agent name
  - entity: notification
    effect: creates
    facts:
    - Kind
    - Subject
    - From
    - Read
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: desk/src/components/ticket-agent/AssignTo.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Assign agents to a ticket

## Trigger

An Agent picks who should work a Ticket.

## Outcome

The chosen Agents are assigned and told about it.

## Edge cases

- Choosing an away or unavailable agent shows a warning but still assigns them.
- With Restrict agent assignment to team on and tickets restricted by team, assignees come from the ticket team's members.
- Assigning oneself sends no notification email.
