---
availability:
- place: helpdesk-web::customer-portal
- place: helpdesk-web::agent-portal
- place: support-email
domain: tickets
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/api.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
- kind: code
  role: implementation
  target: desk/src/pages/ticket/TicketNew.vue
---

# Raise ticket

Raise a support ticket: a requester in the customer portal or by emailing the support address, or an agent in the agent portal. The new ticket takes its type, priority, status, customer and SLA policy, and may be assigned automatically.
