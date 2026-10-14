---
availability:
- place: helpdesk-web::customer-portal
domain: tickets
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
- kind: code
  role: implementation
  target: desk/src/pages/ticket/TicketCustomer.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Close ticket

Close a ticket from the customer portal, rating the support when the Helpdesk asks for it, or have the Product close stale tickets on its daily schedule.
