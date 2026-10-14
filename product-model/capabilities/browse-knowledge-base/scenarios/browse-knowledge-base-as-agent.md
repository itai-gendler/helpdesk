---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent browses Categories and filters Articles by status
  kind: actor
  actor: agent
  entities:
  - entity: article-category
    effect: reads
    facts:
    - Name
  - entity: article
    effect: reads
    facts:
    - Title
    - Category
    - Author
    - Views
  contexts:
    main:
      place: helpdesk-web::agent-portal::knowledge-base
references:
- kind: code
  role: implementation
  target: desk/src/pages/knowledge-base/KnowledgeBaseAgent.vue
- kind: code
  role: implementation
  target: helpdesk/api/article.py
---

# Browse the knowledge base as an agent

## Trigger

An Agent opens the knowledge base.

## Outcome

The Agent sees every Article by Category and status, with views and feedback counts.
