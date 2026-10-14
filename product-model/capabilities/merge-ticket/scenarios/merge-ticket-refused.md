---
kind: validation
routes:
  main: Agent portal
steps:
- text: The Agent chooses a target Ticket
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Merged with
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product refuses because the Ticket is already merged or is its own target
  kind: condition
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Merged with
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/api.py
---

# Refuse an invalid merge

## Trigger

An Agent tries to merge a Ticket that is already merged, or into itself.

## Outcome

Nothing is merged and the Agent is told why.

## Edge cases

- The agent must be allowed to change both tickets.
