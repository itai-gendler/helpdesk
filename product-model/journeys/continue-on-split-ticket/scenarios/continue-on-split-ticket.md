---
kind: primary
result: achieved
routes:
  main: Agent portal
steps:
- text: The Agent splits the Ticket from a Reply
  kind: actor
  actor: agent
  entities:
  - entity: reply
    effect: reads
    facts: []
  - entity: ticket
    effect: creates
    to: Open
    facts:
    - Subject
    - Status
    - Priority
    - Ticket type
    - Team
    - Raised by
    - Customer
    - Split from
    - SLA policy
    - SLA clock start
    - First response due
    - Resolution due
    - SLA status
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
  capability: split-ticket
- text: The Product opens the new Ticket
  kind: product
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
  capability: split-ticket
- text: The Agent replies on the new Ticket
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

# Split a ticket and reply on the new one

## Trigger

An Agent splits a ticket from a reply.

## Outcome

The Agent is on the new ticket and has replied there.
