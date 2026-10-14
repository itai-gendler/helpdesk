---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent writes a note, mentioning other agents
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Subject
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product adds the Comment and keeps its files with the Comment
  kind: product
  actor: agent
  entities:
  - entity: comment
    effect: creates
    facts:
    - Content
    - Author
    - Mentions
    - Attachments
    - Pinned
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product notifies each mentioned Agent
  kind: product
  actor: agent
  entities:
  - entity: comment
    effect: reads
    facts:
    - Mentions
  - entity: agent
    effect: reads
    facts: []
  - entity: notification
    effect: creates
    facts:
    - Kind
    - Subject
    - From
    - Read
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/extends/comment.py
- kind: code
  role: implementation
  target: helpdesk/utils.py
---

# Comment on a ticket

## Trigger

An Agent wants to note something for the team on a Ticket.

## Outcome

The Comment shows in the Ticket's activity for agents, and mentioned agents are notified.
