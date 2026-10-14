---
entities:
- entity: article
  shows:
  - Title
  - Category
  - Author
  - Views
- entity: article-category
  shows:
  - Name
  collects:
  - Name
entryPoints:
- helpdesk-web: /helpdesk/kb
references:
- kind: code
  role: implementation
  target: desk/src/pages/knowledge-base/KnowledgeBaseAgent.vue
---

# Knowledge Base

Agents' view of all articles by category and status.
