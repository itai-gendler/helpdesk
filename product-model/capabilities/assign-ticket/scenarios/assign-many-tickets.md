---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent selects Tickets and chooses Agents
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Subject
    - Assigned agents
  - entity: agent
    effect: reads
    facts:
    - Agent name
  contexts:
    main:
      place: helpdesk-web::agent-portal::tickets
- text: The Product assigns the chosen Agents to each selected Ticket
  kind: product
  actor: agent
  entities:
  - entity: ticket
    effect: changes
    facts:
    - Assigned agents
  contexts:
    main:
      place: helpdesk-web::agent-portal::tickets
references:
- kind: code
  role: implementation
  target: desk/src/components/ticket-agent/BulkAssignModal.vue
---

# Assign several tickets at once

## Trigger

An Agent selects several Tickets in the ticket list and chooses assignees.

## Outcome

Each selected Ticket has the chosen assignees.
