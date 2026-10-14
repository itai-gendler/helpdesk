---
entities:
- entity: helpdesk-settings
  shows: &id001
  - Acknowledgement email
  - Reply from contact email
  - Reply from agent email
  - Share feedback email
  collects: *id001
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/EmailNotifications/EmailNotifications.vue
---

# Email Notifications

The notification emails and their content.
