---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent chooses Publish
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
- text: The Product publishes the Article
  kind: product
  actor: agent
  entities:
  - entity: article
    effect: changes
    from: Draft
    to: Published
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

# Publish an article

## Trigger

An Agent publishes a draft Article.

## Outcome

Requesters can read the Article and it shows when it was published.

## Edge cases

- An article without content cannot be published.
