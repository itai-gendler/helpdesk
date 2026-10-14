---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent edits the title and content and saves
  kind: actor
  actor: agent
  entities:
  - entity: article
    effect: reads
    facts:
    - Title
    - Content
  contexts:
    main:
      place: helpdesk-web::agent-portal::article
- text: The Product saves the Article
  kind: product
  actor: agent
  entities:
  - entity: article
    effect: changes
    facts:
    - Title
    - Content
  contexts:
    main:
      place: helpdesk-web::agent-portal::article
references:
- kind: code
  role: implementation
  target: desk/src/pages/knowledge-base/Article.vue
---

# Edit an article

## Trigger

An Agent corrects an Article.

## Outcome

The Article shows the new title and content.
