---
entities:
- entity: ticket
  shows:
  - Subject
  - Status
  - Priority
  - Ticket type
  - Team
  - Template fields
  - Feedback
  collects:
  - Template fields
  - Feedback
  - Rating
  - Feedback comment
- entity: reply
  shows:
  - Message
  - Sender
  - Attachments
  - Sent at
  collects:
  - Message
  - Attachments
entryPoints:
- helpdesk-web: /helpdesk/my-tickets/:ticketId
references:
- kind: code
  role: implementation
  target: desk/src/pages/ticket/TicketCustomer.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/api.py
---

# Ticket

One of the requester's tickets: its conversation, the details visible to customers, and the reply box while the ticket is open to them.
