---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent picks an emoji on the Comment
  kind: actor
  actor: agent
  entities:
  - entity: comment
    effect: reads
    facts:
    - Content
    - Reactions
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product records the Agent's reaction and notifies the Comment's author
  kind: product
  actor: agent
  entities:
  - entity: comment
    effect: changes
    facts:
    - Reactions
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
  target: helpdesk/api/comment.py
- kind: code
  role: implementation
  target: helpdesk/notifications.py
---

# React to a comment

## Trigger

An Agent reacts to a Comment while comment reactions are on.

## Outcome

The Comment shows the reaction live and its author is notified.

## Edge cases

- Picking the same emoji again removes the reaction; picking another changes it. Each agent keeps one reaction per comment.
