---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Administrator chooses Delete and confirms
  kind: actor
  actor: administrator
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Subject
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product deletes the Ticket
  kind: product
  actor: administrator
  entities:
  - entity: ticket
    effect: removes
    from: Closed
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/api/ticket.py
---

# Delete a ticket

## Trigger

The Administrator deletes a Ticket and confirms.

## Outcome

The Ticket is gone.

## Edge cases

- A ticket in any state may be deleted.
