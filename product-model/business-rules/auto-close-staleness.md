---
appliesTo:
- type: capability-scenario
  id: close-stale-ticket
- type: entity
  id: helpdesk-settings
  facts:
  - Auto-close
  - Auto-close status
  - Auto-close after days
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_settings/hd_settings.py
---

# Tickets idle in the auto-close status close after the configured days

With auto-close on, a ticket in the auto-close status whose last message is older than the configured number of days is closed once a day; a ticket with no message at all is never auto-closed.
