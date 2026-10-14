---
entities:
- entity: article
  collects:
  - Title
  - Content
  - Category
- entity: article-category
  shows:
  - Name
entryPoints:
- helpdesk-web: /helpdesk/articles/new/:id
references:
- kind: code
  role: implementation
  target: desk/src/pages/knowledge-base/NewArticle.vue
---

# New article

Writing a new article in a category.
