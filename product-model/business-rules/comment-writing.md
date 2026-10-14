---
appliesTo:
- type: entity
  id: comment
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
  target: helpdesk/extends/comment.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Only agents comment on tickets

Comments are internal notes; adding one is refused to anyone without agent access.
