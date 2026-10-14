---
appliesTo:
- type: entity
  id: notification
  effect: removes
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
---

# Notifications go with the comment that raised them

Deleting a comment removes the notifications it raised, whoever received them.
