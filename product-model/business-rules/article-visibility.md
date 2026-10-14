---
appliesTo:
- type: entity
  id: article
  effect: reads
permits:
- actors:
  - agent
  - agent-manager
  - system-manager
  - administrator
- actors:
  - contact
  when:
  - state: Published
references:
- kind: code
  role: implementation
  target: helpdesk/api/knowledge_base.py
- kind: code
  role: implementation
  target: helpdesk/api/article.py
---

# Requesters read published articles; agents read every article

Draft articles, and their view and feedback counts, are for agents only.
