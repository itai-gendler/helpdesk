---
availability:
- place: helpdesk-web::agent-portal
domain: tickets
references:
- kind: code
  role: implementation
  target: helpdesk/api/doc.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Unassign ticket

Take agents off a ticket, by hand or when the ticket meets an assignment rule's unassignment condition.
