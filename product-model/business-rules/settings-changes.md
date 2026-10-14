---
appliesTo:
- type: entity
  id: helpdesk-settings
  effect: changes
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_settings/hd_settings.json
- kind: code
  role: implementation
  target: helpdesk/api/settings/email_notifications.py
---

# Agent Managers and System Managers change the Helpdesk settings

The settings menu shows General only to System Managers and Email Notifications to both.
