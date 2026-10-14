---
kind: validation
routes:
  main: Customer portal
steps:
- text: The Contact submits a change to a locked field
  kind: actor
  actor: contact
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Template fields
  contexts:
    main:
      place: helpdesk-web::customer-portal::ticket
- text: The Product refuses the change
  kind: condition
  actor: contact
  entities:
  - entity: ticket
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::customer-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
---

# Refuse a requester's change to a locked field

## Trigger

A Contact tries to change a field of their Ticket that the template does not leave editable.

## Outcome

Nothing changes; the Contact is told the field cannot change after the ticket is raised, or that they lack permission for it.
