---
kind: primary
routes:
  main: Customer portal
steps:
- text: The Contact enters a subject, a description and the fields the template asks for
  kind: actor
  actor: contact
  entities: []
  contexts:
    main:
      place: helpdesk-web::customer-portal::new-ticket
- text: The Product creates the Ticket in its policy's default status, with the Contact's opening Reply
  kind: product
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
  - entity: reply
    effect: creates
    facts:
    - Message
    - Sender
    - Direction
    - Sent at
    with: ticket
  contexts:
    main:
      place: helpdesk-web::customer-portal::new-ticket
- text: The new Ticket opens in the portal
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
  target: helpdesk/helpdesk/doctype/hd_ticket/api.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/utils.py
---

# Raise a ticket in the customer portal

## Trigger

A signed-in Contact needs help and opens New Ticket in the customer portal.

## Outcome

The Contact's new Ticket is open, timed by its SLA policy, and shown to them in the portal.

## Decision points

### Customer

Did the requester choose a customer?

- A customer was chosen → the ticket keeps it
- None was chosen, auto-set is on and the contact belongs to exactly one customer → the ticket takes that customer
- Otherwise → the ticket has no customer

### Automatic assignment

Does an enabled assignment rule active today match the new ticket?

- A rule matches → the ticket is assigned by that rule's routing, highest-priority rule first
- No rule matches → the ticket stays unassigned

## Edge cases

- Articles matching the subject are suggested while the ticket is being written.
- A ticket raised outside its policy's working hours is marked so, and its requester sees the outside working hours notice when it is on.
- The first ticket a requester ever raises is tagged as their first ticket.
