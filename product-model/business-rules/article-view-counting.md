---
appliesTo:
- type: entity
  id: article
  effect: changes
  facts:
  - Views
permits:
- actors:
  - contact
- actors:
  - agent
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/api/knowledge_base.py
---

# Requesters' opens count as article views

The Product counts views as requesters open articles, at most once an hour per person.
