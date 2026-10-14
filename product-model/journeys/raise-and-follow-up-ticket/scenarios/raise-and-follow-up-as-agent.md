---
kind: primary
result: achieved
routes:
  main: Agent portal
steps:
- text: The Agent submits a new ticket
  kind: actor
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
  contexts:
    main:
      place: helpdesk-web::agent-portal::new-ticket
  capability: raise-ticket
- text: The Product opens the new Ticket's page
  kind: product
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
  capability: raise-ticket
- text: The Agent replies on the Ticket
  kind: actor
  actor: agent
  entities:
  - entity: reply
    effect: creates
    facts:
    - Message
    - Sender
    - Direction
    - To
    - CC
    - BCC
    - Attachments
    - Sent at
  - entity: ticket
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
  capability: reply-to-ticket
---

# Raise a ticket as an agent and reply on it

## Trigger

An Agent raises a ticket in the agent portal.

## Outcome

The Agent is on the new ticket's page and has replied on it.
