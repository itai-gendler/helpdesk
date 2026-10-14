---
availability:
- place: helpdesk-web::agent-portal
domain: knowledge-base
references:
- kind: code
  role: implementation
  target: desk/src/pages/knowledge-base/KnowledgeBaseAgent.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article_category/hd_article_category.py
---

# Delete category

Delete a category; its articles move to General.
