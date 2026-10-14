---
entities:
- entity: notification
  shows:
  - Kind
  - Subject
  - From
  - Read
entryPoints:
- helpdesk-web: /helpdesk/notifications
references:
- kind: code
  role: implementation
  target: desk/src/pages/MobileNotifications.vue
- kind: code
  role: implementation
  target: desk/src/components/notifications/Notifications.vue
---

# Notifications

An agent's notifications.
