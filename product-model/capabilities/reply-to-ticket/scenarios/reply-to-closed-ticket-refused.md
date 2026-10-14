---
kind: validation
routes:
  main: Customer portal
steps:
- text: The Contact opens the Ticket
  kind: actor
  actor: contact
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Status
  contexts:
    main:
      place: helpdesk-web::customer-portal::ticket
- text: The Product offers no way to answer because the Ticket is Closed or rated
  kind: condition
  actor: contact
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Status
    - Feedback
  contexts:
    main:
      place: helpdesk-web::customer-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
- kind: code
  role: implementation
  target: desk/src/pages/ticket/TicketCustomer.vue
---

# Refuse a portal reply on a closed or rated ticket

## Trigger

A Contact opens a Ticket that is Closed, or that they have already rated.

## Outcome

The Contact cannot add a reply in the portal.
