---
kind: primary
result: achieved
routes:
  main: Agent portal
steps:
- text: The Agent merges the Ticket into another
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: changes
    from: Open
    to: Closed
    facts:
    - Status
    - Merged with
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
  capability: merge-ticket
- text: The Product opens the target Ticket
  kind: product
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
  capability: merge-ticket
- text: The Agent replies on the target Ticket
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

# Merge a ticket and reply on the target

## Trigger

An Agent merges a duplicate ticket.

## Outcome

The Agent is on the target ticket and has replied there.
