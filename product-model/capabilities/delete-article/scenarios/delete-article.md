---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent selects Articles and confirms Delete
  kind: actor
  actor: agent
  entities:
  - entity: article
    effect: reads
    facts:
    - Title
  contexts:
    main:
      place: helpdesk-web::agent-portal::knowledge-base
- text: The Product deletes the Articles
  kind: product
  actor: agent
  entities:
  - entity: article
    effect: removes
    from: Draft
  contexts:
    main:
      place: helpdesk-web::agent-portal::knowledge-base
references:
- kind: code
  role: implementation
  target: helpdesk/api/knowledge_base.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article/hd_article.py
---

# Delete articles

## Trigger

An Agent selects Articles and deletes them.

## Outcome

The Articles are gone.

## Edge cases

- The last article of a category cannot be deleted.
