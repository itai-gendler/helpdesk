---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent deletes the Comment and confirms
  kind: actor
  actor: agent
  entities:
  - entity: comment
    effect: reads
    facts:
    - Content
    - Author
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product removes the Comment and its notifications
  kind: product
  actor: agent
  entities:
  - entity: comment
    effect: removes
  - entity: notification
    effect: removes
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/extends/comment.py
---

# Delete a comment

## Trigger

An Agent removes a Comment they wrote.

## Outcome

The Comment and the notifications it raised are gone.

## Edge cases

- The comment row offers Delete only on the agent's own comments.
