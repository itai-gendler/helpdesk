---
entities:
- entity: article-category
  shows:
  - Name
- entity: article
  shows:
  - Title
  - Published on
  - Author
entryPoints:
- helpdesk-web: /helpdesk/kb-public/:categoryId
references:
- kind: code
  role: implementation
  target: desk/src/pages/knowledge-base/Articles.vue
---

# Category

The published articles of one category.
