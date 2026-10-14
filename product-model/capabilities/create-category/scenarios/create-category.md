---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent enters a name
  kind: actor
  actor: agent
  entities: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::knowledge-base
- text: The Product creates the Category
  kind: product
  actor: agent
  entities:
  - entity: article-category
    effect: creates
    facts:
    - Name
    - Description
  contexts:
    main:
      place: helpdesk-web::agent-portal::knowledge-base
references:
- kind: code
  role: implementation
  target: helpdesk/api/knowledge_base.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article_category/hd_article_category.py
---

# Create a category

## Trigger

An Agent adds a Category.

## Outcome

The Category exists.

## Edge cases

- General is reserved and refused as a new name.
