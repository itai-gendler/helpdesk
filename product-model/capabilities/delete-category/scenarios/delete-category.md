---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent chooses Delete and confirms
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
- text: The Product moves the Category's Articles to General and deletes the Category
  kind: product
  actor: agent
  entities:
  - entity: article
    effect: changes
    facts:
    - Category
  - entity: article-category
    effect: removes
  contexts:
    main:
      place: helpdesk-web::agent-portal::knowledge-base
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article_category/hd_article_category.py
---

# Delete a category

## Trigger

An Agent deletes a Category.

## Outcome

The Category is gone and its Articles are filed under General.

## Edge cases

- The General category cannot be deleted.
