---
availability:
- place: helpdesk-web::agent-portal
domain: knowledge-base
references:
- kind: code
  role: implementation
  target: helpdesk/api/knowledge_base.py
- kind: code
  role: implementation
  target: desk/src/components/knowledge-base/MergeCategoryModal.vue
---

# Merge category

Merge a category into another: its articles move and the category is deleted.
