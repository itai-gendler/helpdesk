---
appliesTo:
- type: entity
  id: comment
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
  target: helpdesk/setup/comments.py
- kind: code
  role: implementation
  target: helpdesk/extends/comment.py
---

# Agents edit, pin and delete ticket comments

Agents moderate the internal notes on the tickets they work.
