---
entities:
- entity: article-category
  shows:
  - Name
  - Description
- entity: article
  shows:
  - Title
entryPoints:
- helpdesk-web: /helpdesk/kb-public
references:
- kind: code
  role: implementation
  target: desk/src/pages/knowledge-base/KnowledgeBaseCustomer.vue
---

# Knowledge Base

The requesters' knowledge base: categories and search.
