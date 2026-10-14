---
kind: primary
routes:
  main: Customer portal
steps:
- text: The Contact opens a Category or searches
  kind: actor
  actor: contact
  entities:
  - entity: article-category
    effect: reads
    facts:
    - Name
    - Description
  - entity: article
    effect: reads
    facts:
    - Title
  contexts:
    main:
      place: helpdesk-web::customer-portal::knowledge-base
- text: The Contact picks an Article in the Category
  kind: actor
  actor: contact
  entities:
  - entity: article-category
    effect: reads
    facts:
    - Name
  - entity: article
    effect: reads
    facts:
    - Title
    - Published on
    - Author
  contexts:
    main:
      place: helpdesk-web::customer-portal::category
- text: The Contact opens an Article
  kind: actor
  actor: contact
  entities:
  - entity: article
    effect: reads
    facts:
    - Title
    - Content
    - Category
    - Author
    - Published on
  contexts:
    main:
      place: helpdesk-web::customer-portal::article
- text: The Product counts the view
  kind: product
  actor: contact
  entities:
  - entity: article
    effect: changes
    facts:
    - Views
  contexts:
    main:
      place: helpdesk-web::customer-portal::article
references:
- kind: code
  role: implementation
  target: helpdesk/api/knowledge_base.py
- kind: code
  role: implementation
  target: desk/src/pages/knowledge-base/Article.vue
---

# Read an article in the customer portal

## Trigger

A Contact looks for an answer in the knowledge base.

## Outcome

The Contact reads a published Article, whose view count goes up.

## Edge cases

- Draft articles are never shown to requesters.
- Repeated opens by the same person within an hour count once.
