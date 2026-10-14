---
availability:
- place: helpdesk-web::agent-portal
domain: tickets
references:
- kind: code
  role: implementation
  target: desk/src/components/ticket-agent/AssignTo.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/overrides/assignment_rule.py
---

# Assign ticket

Put agents on a ticket, by hand from the ticket or the ticket list, or automatically through the assignment rules when a ticket is saved.
