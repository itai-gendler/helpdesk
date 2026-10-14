---
entities:
- entity: article
  shows:
  - Title
  - Content
  - Category
  - Author
  - Published on
  - Views
  collects:
  - Title
  - Content
entryPoints:
- helpdesk-web: /helpdesk/kb/articles/:articleId
references:
- kind: code
  role: implementation
  target: desk/src/pages/knowledge-base/Article.vue
---

# Article

One article as agents see it, with its status, views and feedback, and its editor.
