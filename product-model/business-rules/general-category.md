---
appliesTo:
- type: capability
  id: rename-category
- type: capability
  id: delete-category
- type: capability
  id: merge-category
- type: capability
  id: create-category
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article_category/hd_article_category.py
- kind: code
  role: implementation
  target: helpdesk/api/knowledge_base.py
---

# The General category always exists under its name

General cannot be renamed, deleted or merged away, and no other category may take its name; a deleted category's articles move to it.
