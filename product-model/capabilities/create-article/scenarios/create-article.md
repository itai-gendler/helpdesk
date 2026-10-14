---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent writes a title and content in a Category
  kind: actor
  actor: agent
  entities:
  - entity: article-category
    effect: reads
    facts:
    - Name
  contexts:
    main:
      place: helpdesk-web::agent-portal::new-article
- text: The Product creates the draft Article with the Agent as author
  kind: product
  actor: agent
  entities:
  - entity: article
    effect: creates
    to: Draft
    facts:
    - Title
    - Content
    - Category
    - Author
  contexts:
    main:
      place: helpdesk-web::agent-portal::new-article
- text: The new Article opens
  kind: condition
  actor: agent
  entities:
  - entity: article
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::article
references:
- kind: code
  role: implementation
  target: desk/src/pages/knowledge-base/NewArticle.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article/hd_article.py
---

# Create an article

## Trigger

An Agent adds an article to a Category.

## Outcome

The draft Article exists and opens on its page.

## Edge cases

- A title and content are required.
