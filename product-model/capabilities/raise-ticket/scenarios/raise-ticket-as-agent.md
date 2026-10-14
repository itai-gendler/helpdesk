---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent enters a subject, a description and the template's fields
  kind: actor
  actor: agent
  entities: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::new-ticket
- text: The Product creates the Ticket raised by the Agent, with its opening Reply
  kind: product
  actor: agent
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
      place: helpdesk-web::agent-portal::new-ticket
- text: The new Ticket opens
  kind: condition
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/api.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Raise a ticket in the agent portal

## Trigger

An Agent opens New Ticket in the agent portal.

## Outcome

The Agent's new Ticket is open, raised by the Agent, and opened for them in the agent portal; no acknowledgement is emailed.

## Decision points

### Automatic assignment

Does an enabled assignment rule active today match the new ticket?

- A rule matches → the ticket is assigned by that rule's routing, highest-priority rule first
- No rule matches → the ticket stays unassigned
