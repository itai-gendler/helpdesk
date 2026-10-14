---
appliesTo:
- type: entity
  id: notification
  effect: reads
permits:
- related:
  - verb: receives
    entity: agent
references:
- kind: code
  role: implementation
  target: helpdesk/notifications.py
---

# Agents read only their own notifications

Each notification belongs to the agent it was raised for.
