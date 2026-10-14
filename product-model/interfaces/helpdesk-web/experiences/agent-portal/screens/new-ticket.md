---
entities:
- entity: ticket
  collects:
  - Subject
  - Description
  - Template fields
entryPoints:
- helpdesk-web: /helpdesk/tickets/new/:templateId
references:
- kind: code
  role: implementation
  target: desk/src/pages/ticket/TicketNew.vue
---

# New ticket

Where an agent raises a ticket from a ticket template.
