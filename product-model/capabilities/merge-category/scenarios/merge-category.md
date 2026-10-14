---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent picks the Category to merge into
  kind: actor
  actor: agent
  entities:
  - entity: article-category
    as: target
    effect: reads
    facts:
    - Name
  contexts:
    main:
      place: helpdesk-web::agent-portal::knowledge-base
- text: The Product moves the source's Articles to the target and deletes the source Category
  kind: product
  actor: agent
  entities:
  - entity: article
    effect: changes
    facts:
    - Category
  - entity: article-category
    as: source
    effect: removes
  - entity: article-category
    as: target
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::knowledge-base
references:
- kind: code
  role: implementation
  target: helpdesk/api/knowledge_base.py
---

# Merge a category into another

## Trigger

An Agent merges a Category into another.

## Outcome

The target Category holds the Articles and the source Category is gone.

## Edge cases

- General cannot be merged away, and a category cannot be merged into itself.
