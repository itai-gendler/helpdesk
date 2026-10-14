---
kind: primary
routes:
  main: Customer portal
steps:
- text: The Contact changes an editable field
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
- text: The Product saves the field
  kind: product
  actor: contact
  entities:
  - entity: ticket
    effect: changes
    facts:
    - Template fields
  contexts:
    main:
      place: helpdesk-web::customer-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
---

# Change an editable field in the portal

## Trigger

A Contact changes a template field left editable after the Ticket was raised.

## Outcome

The Ticket keeps the Contact's new value.
