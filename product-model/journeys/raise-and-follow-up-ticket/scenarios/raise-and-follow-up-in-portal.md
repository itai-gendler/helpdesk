---
kind: primary
result: achieved
routes:
  main: Customer portal
steps:
- text: The Contact submits a new ticket
  kind: actor
  actor: contact
  entities:
  - entity: ticket
    effect: creates
    to: Open
    facts:
    - Subject
    - Description
    - Status
    - Priority
    - Ticket type
    - Raised by
    - Customer
    - Raised via portal
    - Raised outside working hours
    - Template fields
    - SLA policy
    - SLA clock start
    - First response due
    - Resolution due
    - SLA status
  contexts:
    main:
      place: helpdesk-web::customer-portal::new-ticket
  capability: raise-ticket
- text: The Product opens the new Ticket's page
  kind: product
  actor: contact
  entities:
  - entity: ticket
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::customer-portal::ticket
  capability: raise-ticket
- text: The Contact adds a Reply on the Ticket
  kind: actor
  actor: contact
  entities:
  - entity: reply
    effect: creates
    facts:
    - Message
    - Sender
    - Direction
    - Attachments
    - Sent at
  - entity: ticket
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::customer-portal::ticket
  capability: reply-to-ticket
---

# Raise a ticket in the portal and reply on it

## Trigger

A Contact raises a ticket in the customer portal.

## Outcome

The Contact is on the new ticket's page and has added a reply.
