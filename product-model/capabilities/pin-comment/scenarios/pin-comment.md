---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent pins the Comment
  kind: actor
  actor: agent
  entities:
  - entity: comment
    effect: reads
    facts:
    - Content
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product pins the Comment
  kind: product
  actor: agent
  entities:
  - entity: comment
    effect: changes
    facts:
    - Pinned
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/extends/comment.py
---

# Pin a comment

## Trigger

An Agent wants a Comment to stay in view on the Ticket.

## Outcome

The Comment is pinned at the top of the Ticket's activity.
