---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent removes a tag
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Tags
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product removes the tag from the Ticket
  kind: product
  actor: agent
  entities:
  - entity: ticket
    effect: changes
    facts:
    - Tags
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/api/tags.py
---

# Remove a tag from a ticket

## Trigger

An Agent removes a tag from a Ticket.

## Outcome

The Ticket no longer carries the tag.
