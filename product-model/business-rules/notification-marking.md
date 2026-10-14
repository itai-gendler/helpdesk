---
appliesTo:
- type: entity
  id: notification
  effect: changes
permits:
- related:
  - verb: receives
    entity: agent
references:
- kind: code
  role: implementation
  target: helpdesk/notifications.py
---

# Agents mark only their own notifications read

Self-assignment and one's own actions raise no notification.
