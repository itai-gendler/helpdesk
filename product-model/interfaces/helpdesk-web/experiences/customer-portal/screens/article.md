---
entities:
- entity: article
  shows:
  - Title
  - Content
  - Category
  - Author
  - Published on
- entity: article-feedback
  shows:
  - Feedback
  collects:
  - Feedback
entryPoints:
- helpdesk-web: /helpdesk/kb-public/articles/:articleId
references:
- kind: code
  role: implementation
  target: desk/src/pages/knowledge-base/Article.vue
---

# Article

One published article and whether it helped.
