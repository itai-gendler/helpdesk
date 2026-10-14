---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent unpins the Comment
  kind: actor
  actor: agent
  entities:
  - entity: comment
    effect: reads
    facts:
    - Content
    - Pinned
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product unpins the Comment
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

# Unpin a comment

## Trigger

A pinned Comment no longer needs to stay in view.

## Outcome

The Comment returns to its place in the activity.
