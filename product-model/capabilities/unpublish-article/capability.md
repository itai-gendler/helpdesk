---
availability:
- place: helpdesk-web::agent-portal
domain: knowledge-base
references:
- kind: code
  role: implementation
  target: desk/src/pages/knowledge-base/Article.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article/hd_article.py
---

# Unpublish article

Take a published article back to draft.
