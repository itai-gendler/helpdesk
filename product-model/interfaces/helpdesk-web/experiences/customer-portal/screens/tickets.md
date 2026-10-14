---
entities:
- entity: ticket
  shows:
  - Subject
  - Status
  - Priority
  - First response due
  - Resolution due
  - Team
entryPoints:
- helpdesk-web: /helpdesk/my-tickets
references:
- kind: code
  role: implementation
  target: desk/src/pages/ticket/Tickets.vue
---

# My tickets

The requester's ticket list.
