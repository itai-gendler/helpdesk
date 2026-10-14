---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent edits the Comment's text
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
- text: The Product saves the Comment
  kind: product
  actor: agent
  entities:
  - entity: comment
    effect: changes
    facts:
    - Content
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: desk/src/components/ticket-agent/timeline/TimelineCommentRow.vue
---

# Edit a comment

## Trigger

An Agent corrects a Comment they wrote.

## Outcome

The Comment shows the new text.

## Edge cases

- The comment row offers Edit only on the agent's own comments.
