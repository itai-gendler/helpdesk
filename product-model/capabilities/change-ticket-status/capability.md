---
availability:
- place: helpdesk-web::agent-portal
domain: tickets
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.py
- kind: code
  role: implementation
  target: desk/src/components/ticket-agent/TicketHeader.vue
---

# Change ticket status

Move a ticket to any enabled status from the agent portal. The status's category decides the ticket's state: Open runs the SLA clock, Paused holds it, Resolved stamps the resolution.
