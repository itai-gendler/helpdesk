---
entities:
- entity: ticket
  shows:
  - Subject
  - Status
  - Priority
  - Ticket type
  - Team
  - Customer
  - Assigned agents
  - First response due
  - Resolution due
  - SLA status
  - Rating
- entity: reply
  collects:
  - Message
  - Attachments
- entity: agent
  shows:
  - Agent name
entryPoints:
- helpdesk-web: /helpdesk/tickets
references:
- kind: code
  role: implementation
  target: desk/src/pages/ticket/Tickets.vue
- kind: code
  role: implementation
  target: desk/src/components/ticket-agent/BulkReplyModal.vue
---

# Tickets

The agent ticket list with filters, sorting, saved views and actions on selected tickets.
