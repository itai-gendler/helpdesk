---
appliesTo:
- type: entity
  id: saved-reply
  effect: changes
permits:
- actors:
  - agent
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_saved_reply/hd_saved_reply.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_saved_reply/hd_saved_reply.json
---

# Agents change saved replies

Saved replies are an agents' tool; requesters never see them.
