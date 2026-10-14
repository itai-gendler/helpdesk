---
kind: primary
routes:
  main: Customer portal
steps:
- text: The Contact chooses Close and confirms
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
- text: The Product closes the Ticket
  kind: product
  actor: contact
  entities:
  - entity: ticket
    effect: changes
    from: Open
    to: Closed
    facts:
    - Status
    - Resolution date
    - Resolution time
    - SLA status
  contexts:
    main:
      place: helpdesk-web::customer-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Close a ticket after confirming

## Trigger

A Contact closes a Ticket while feedback is not mandatory or no agent has replied yet.

## Outcome

The Ticket is Closed.
