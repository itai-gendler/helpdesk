---
entities:
- entity: ticket
  collects:
  - Subject
  - Description
  - Customer
  - Template fields
- entity: customer
  shows:
  - Customer name
entryPoints:
- helpdesk-web: /helpdesk/my-tickets/new
references:
- kind: code
  role: implementation
  target: desk/src/pages/ticket/TicketNew.vue
---

# New ticket

Where a requester raises a ticket, guided by the ticket template and suggested articles.
