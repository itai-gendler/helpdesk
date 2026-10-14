---
availability:
- place: helpdesk-web::agent-portal
- place: helpdesk-web::customer-portal
domain: tickets
references:
- kind: code
  role: implementation
  target: desk/src/pages/ticket/Tickets.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Browse tickets

List, filter and open the tickets one may see: agents in the agent portal, requesters their own tickets in the customer portal.
