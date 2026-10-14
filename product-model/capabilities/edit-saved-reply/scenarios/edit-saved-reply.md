---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent changes the Saved reply and saves
  kind: actor
  actor: agent
  entities:
  - entity: saved-reply
    effect: reads
    facts:
    - Title
    - Message
    - Scope
    - Teams
    - Actions
  contexts:
    main:
      place: helpdesk-web::agent-portal::saved-reply
- text: The Product saves the Saved reply
  kind: product
  actor: agent
  entities:
  - entity: saved-reply
    effect: changes
    facts:
    - Title
    - Message
    - Scope
    - Teams
    - Actions
  contexts:
    main:
      place: helpdesk-web::agent-portal::saved-reply
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_saved_reply/hd_saved_reply.py
---

# Edit a saved reply

## Trigger

An Agent improves a Saved reply.

## Outcome

The Saved reply has the new content.

## Edge cases

- An action whose status, team, type or agent was later disabled keeps working for unrelated edits.
