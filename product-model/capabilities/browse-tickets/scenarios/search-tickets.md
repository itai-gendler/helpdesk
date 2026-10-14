---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent enters at least two characters and optional filters
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Subject
    - Status
  - entity: reply
    effect: reads
    facts:
    - Message
  - entity: comment
    effect: reads
    facts:
    - Content
  contexts:
    main:
      place: helpdesk-web::agent-portal::search
references:
- kind: code
  role: implementation
  target: helpdesk/api/search.py
- kind: code
  role: implementation
  target: helpdesk/search_sqlite.py
---

# Search tickets

## Trigger

An Agent searches for a phrase across tickets.

## Outcome

The Agent sees matching Tickets, Replies and Comments among the tickets they may see.

## Edge cases

- While the search index is being built, the search is unavailable.
