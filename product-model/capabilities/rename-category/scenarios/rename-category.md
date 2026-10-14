---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent enters a new title
  kind: actor
  actor: agent
  entities:
  - entity: article-category
    effect: reads
    facts:
    - Name
  contexts:
    main:
      place: helpdesk-web::agent-portal::knowledge-base
- text: The Product renames the Category
  kind: product
  actor: agent
  entities:
  - entity: article-category
    effect: changes
    facts:
    - Name
  contexts:
    main:
      place: helpdesk-web::agent-portal::knowledge-base
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article_category/hd_article_category.py
---

# Rename a category

## Trigger

An Agent edits a Category's title.

## Outcome

The Category has the new name.

## Edge cases

- The General category cannot be renamed.
