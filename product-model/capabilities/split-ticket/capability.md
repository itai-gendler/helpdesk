---
availability:
- place: helpdesk-web::agent-portal
domain: tickets
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/api.py
- kind: code
  role: implementation
  target: desk/src/components/ticket/TicketSplitModal.vue
---

# Split ticket

Split a ticket's conversation from one reply onwards into a new ticket.
