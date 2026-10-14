---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent chooses Unpublish
  kind: actor
  actor: agent
  entities:
  - entity: article
    effect: reads
    facts:
    - Title
  contexts:
    main:
      place: helpdesk-web::agent-portal::article
- text: The Product returns the Article to draft
  kind: product
  actor: agent
  entities:
  - entity: article
    effect: changes
    from: Published
    to: Draft
    facts:
    - Published on
  contexts:
    main:
      place: helpdesk-web::agent-portal::article
references:
- kind: code
  role: implementation
  target: desk/src/pages/knowledge-base/Article.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article/hd_article.py
---

# Unpublish an article

## Trigger

An Agent unpublishes an Article.

## Outcome

The Article is a draft again and hidden from requesters.
