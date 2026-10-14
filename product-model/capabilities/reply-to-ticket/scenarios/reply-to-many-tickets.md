---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent selects Tickets and writes one message
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Subject
  contexts:
    main:
      place: helpdesk-web::agent-portal::tickets
- text: The Product adds the Reply to each selected Ticket and emails its requester
  kind: product
  actor: agent
  entities:
  - entity: reply
    effect: creates
    facts:
    - Message
    - Sender
    - Direction
    - To
    - Attachments
    - Sent at
  - entity: ticket
    effect: changes
    facts:
    - First responded on
    - First response time
    - Last agent response
    - SLA status
  contexts:
    main:
      place: helpdesk-web::agent-portal::tickets
references:
- kind: code
  role: implementation
  target: helpdesk/api/ticket.py
---

# Reply to several tickets at once

## Trigger

An Agent selects several Tickets in the ticket list and writes one reply.

## Outcome

Each selected Ticket has the Reply, sent to its requester, unless the Agent may not reply to one of them.

## Edge cases

- If the Agent may not reply to any one selected ticket, nothing is written to any of them.
- A ticket selected twice is replied to once.
