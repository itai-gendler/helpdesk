---
kind: validation
routes:
  main: Customer portal
steps:
- text: The Contact submits a new ticket without choosing a Customer
  kind: actor
  actor: contact
  entities:
  - entity: customer
    effect: reads
    facts: []
  - entity: ticket
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::customer-portal::new-ticket
- text: The Product refuses because the Contact belongs to several Customers
  kind: condition
  actor: contact
  entities:
  - entity: customer-membership
    effect: reads
    facts:
    - Role
  - entity: customer
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::customer-portal::new-ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Refuse a portal ticket whose customer is ambiguous

## Trigger

A Contact who belongs to several Customers raises a ticket in the portal without choosing one, while auto-set customer is on.

## Outcome

No Ticket is created; the Contact is asked to choose the customer.

## Edge cases

- A requester naming a customer they do not belong to is refused too.
