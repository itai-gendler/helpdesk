---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent picks a Reply in the conversation and gives a subject
  kind: actor
  actor: agent
  entities:
  - entity: reply
    effect: reads
    facts:
    - Message
    - Sent at
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product creates the new Ticket split from the original, with its SLA restarted
  kind: product
  actor: agent
  entities:
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
- text: The Product moves the Replies, Comments and files from that Reply onwards to the new Ticket and replies on the original with a link
  kind: product
  actor: agent
  entities:
  - entity: reply
    effect: reads
    facts:
    - Sent at
  - entity: comment
    effect: reads
    facts: []
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

# Split a ticket from a reply

## Trigger

An Agent sees that a later message in a Ticket's conversation is a separate issue.

## Outcome

A new open Ticket holds that message and everything after it; the original Ticket tells the requester to follow the new one.
