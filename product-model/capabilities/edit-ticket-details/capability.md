---
availability:
- place: helpdesk-web::agent-portal
- place: helpdesk-web::customer-portal
domain: tickets
references:
- kind: code
  role: implementation
  target: desk/src/components/ticket-agent/TicketDetailsTab.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Edit ticket details

Change a ticket's own details: an agent changes its subject, priority, type, team, customer and template fields; a requester changes only the template fields left editable after the ticket is raised.
