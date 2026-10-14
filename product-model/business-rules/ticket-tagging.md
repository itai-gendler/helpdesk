---
appliesTo:
- type: entity
  id: ticket
  effect: changes
  facts:
  - Tags
permits:
- actors:
  - agent
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/api/tags.py
---

# Agents tag tickets

Tagging needs agent access and permission to change the ticket; requesters never see tags.
