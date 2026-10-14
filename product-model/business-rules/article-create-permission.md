---
appliesTo:
- type: entity
  id: article
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
  target: helpdesk/helpdesk/doctype/hd_article/hd_article.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article/hd_article.json
---

# Agents create knowledge base articles

Requesters only read the knowledge base.
