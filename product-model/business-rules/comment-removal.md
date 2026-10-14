---
appliesTo:
- type: entity
  id: comment
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
  target: helpdesk/setup/comments.py
- kind: code
  role: implementation
  target: helpdesk/extends/comment.py
---

# Agents delete ticket comments

Deleting a comment also clears the notifications it raised.
