---
availability:
- place: helpdesk-web::agent-portal
domain: tickets
references:
- kind: code
  role: implementation
  target: helpdesk/api/ticket.py
- kind: code
  role: implementation
  target: desk/src/components/ticket-agent/TicketHeader.vue
---

# Delete ticket

Delete a ticket for good.
