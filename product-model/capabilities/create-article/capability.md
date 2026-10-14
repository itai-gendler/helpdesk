---
availability:
- place: helpdesk-web::agent-portal
domain: knowledge-base
references:
- kind: code
  role: implementation
  target: desk/src/pages/knowledge-base/NewArticle.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article/hd_article.py
---

# Create article

Write a new article in a category; it starts as a draft.
