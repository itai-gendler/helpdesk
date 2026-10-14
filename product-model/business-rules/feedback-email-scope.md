---
appliesTo:
- type: capability-scenario
  id: resolve-ticket
- type: capability-scenario
  id: close-resolved-ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/api/settings/email_notifications.py
---

# Only email-raised tickets are asked for feedback by email

The share feedback email goes out when an agent moves a ticket into the configured Resolved-category status (Closed by default), only for tickets raised by email and not yet rated.
