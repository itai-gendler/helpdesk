---
availability:
- place: helpdesk-web::agent-portal
references:
- kind: code
  role: implementation
  target: helpdesk/notifications.py
- kind: code
  role: implementation
  target: desk/src/components/notifications/Notifications.vue
---

# Mark notifications as read

Read one's notifications: opening one, or the ticket it is about, marks it read; Mark all as read clears them all.
