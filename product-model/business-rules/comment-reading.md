---
appliesTo:
- type: entity
  id: comment
  effect: reads
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

# Only agents who may read the ticket read its comments

Requesters never see comments, nor the files added with them.
