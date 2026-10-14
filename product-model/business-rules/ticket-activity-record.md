---
appliesTo:
- type: entity
  id: ticket
- type: entity
  id: ticket-activity
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.json
---

# Changes to a ticket are recorded in its activity

Status and field changes, assignments, splits and automatic closing appear in the ticket's activity, with who did them and when.
