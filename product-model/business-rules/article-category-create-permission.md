---
appliesTo:
- type: entity
  id: article-category
  effect: creates
permits:
- actors:
  - agent
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article_category/hd_article_category.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article_category/hd_article_category.json
---

# Agents create knowledge base categories

Requesters only read the knowledge base.
