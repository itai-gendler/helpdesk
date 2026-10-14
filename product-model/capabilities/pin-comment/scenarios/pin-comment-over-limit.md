---
kind: validation
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
- text: The Product refuses because five Comments are already pinned
  kind: condition
  actor: agent
  entities:
  - entity: comment
    effect: reads
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

# Refuse a sixth pinned comment

## Trigger

An Agent pins a Comment on a Ticket that already has five pinned comments.

## Outcome

The Comment stays unpinned and the Agent is told the limit.
