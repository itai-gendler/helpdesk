---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent writes the title and message, picks the scope and teams, and adds actions
  kind: actor
  actor: agent
  entities:
  - entity: team
    effect: reads
    facts:
    - Name
  contexts:
    main:
      place: helpdesk-web::agent-portal::saved-reply
- text: The Product creates the Saved reply
  kind: product
  actor: agent
  entities:
  - entity: saved-reply
    effect: creates
    facts:
    - Title
    - Message
    - Scope
    - Teams
    - Actions
    - Author
  contexts:
    main:
      place: helpdesk-web::agent-portal::saved-reply
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_saved_reply/hd_saved_reply.py
---

# Create a saved reply

## Trigger

An Agent saves a reply they send often.

## Outcome

The Saved reply is offered to everyone its scope reaches.

## Edge cases

- Duplicate actions, two assignment actions, or a tag both added and removed are refused.
