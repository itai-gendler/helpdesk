---
availability:
- place: helpdesk-web::customer-portal
- place: helpdesk-web::agent-portal
- place: support-email
domain: tickets
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/api/ticket.py
- kind: code
  role: implementation
  target: desk/src/pages/ticket/TicketCustomer.vue
---

# Reply to ticket

Add a reply to a ticket's conversation. A requester replies in the customer portal or in the ticket's email thread, which brings the ticket back to the support team; an agent replies from the agent portal, which emails the reply to the requester and counts as the first response.
