---
kind: primary
routes:
  main: Customer portal
steps:
- text: The Contact opens the ticket list
  kind: actor
  actor: contact
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Subject
    - Status
    - Priority
    - First response due
    - Resolution due
    - Team
  contexts:
    main:
      place: helpdesk-web::customer-portal::tickets
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket_status/hd_ticket_status.json
---

# Browse one's own tickets

## Trigger

A Contact opens the ticket list in the customer portal.

## Outcome

The Contact sees the Tickets they raised, and a Customer Manager also sees every Ticket of the Customers they manage.

## Edge cases

- Statuses show their customer label where one is set.
