---
kind: primary
result: achieved
routes:
  main: Agent portal
steps:
- text: The Agent creates the Article
  kind: actor
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
  capability: create-article
- text: The Product opens the new Article
  kind: product
  actor: agent
  entities:
  - entity: article
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::article
  capability: create-article
- text: The Agent publishes the Article
  kind: actor
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
  capability: publish-article
---

# Create an article and publish it

## Trigger

An Agent writes a new article.

## Outcome

The Agent is on the new article's page and has published it.
