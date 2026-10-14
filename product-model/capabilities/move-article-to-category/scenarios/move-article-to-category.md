---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent selects Articles and picks a Category
  kind: actor
  actor: agent
  entities:
  - entity: article
    effect: reads
    facts:
    - Title
    - Category
  - entity: article-category
    effect: reads
    facts:
    - Name
  contexts:
    main:
      place: helpdesk-web::agent-portal::knowledge-base
- text: The Product moves the Articles
  kind: product
  actor: agent
  entities:
  - entity: article
    effect: changes
    facts:
    - Category
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

# Move articles to another category

## Trigger

An Agent moves selected Articles to another Category.

## Outcome

The Articles are filed under the chosen Category.

## Edge cases

- Moving the last article out of a category is refused.
