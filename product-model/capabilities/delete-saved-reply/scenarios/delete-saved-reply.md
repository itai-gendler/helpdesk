---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent chooses Delete and confirms
  kind: actor
  actor: agent
  entities:
  - entity: saved-reply
    effect: reads
    facts:
    - Title
  contexts:
    main:
      place: helpdesk-web::agent-portal::saved-replies
- text: The Product deletes the Saved reply
  kind: product
  actor: agent
  entities:
  - entity: saved-reply
    effect: removes
  contexts:
    main:
      place: helpdesk-web::agent-portal::saved-replies
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/SavedReplies/SavedRepliesList.vue
---

# Delete a saved reply

## Trigger

An Agent removes a Saved reply.

## Outcome

The Saved reply is gone.
