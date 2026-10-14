---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent picks or types a tag
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
- text: The Product adds the tag to the Ticket
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

# Tag a ticket

## Trigger

An Agent labels a Ticket.

## Outcome

The Ticket carries the tag, and its activity records it.

## Edge cases

- A tag may not be empty or contain a comma.
