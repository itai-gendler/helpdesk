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
  - Raised by
  - Assigned agents
  - SLA policy
  - First response due
  - Resolution due
  - SLA status
  - First responded on
  - Resolution date
  - Rating
  - Feedback
  - Feedback comment
  - Merged with
  - Split from
  - Template fields
  - Tags
  collects:
  - Subject
  - Priority
  - Ticket type
  - Team
  - Customer
  - Template fields
  - Status
  - Tags
- entity: reply
  shows:
  - Message
  - Sender
  - Direction
  - To
  - CC
  - BCC
  - Attachments
  - Sent at
  collects:
  - Message
  - To
  - CC
  - BCC
  - Attachments
- entity: comment
  shows:
  - Content
  - Author
  - Mentions
  - Attachments
  - Pinned
  - Reactions
  collects:
  - Content
  - Attachments
  - Reactions
- entity: ticket-activity
  shows:
  - Actor
  - Change
  - Time
- entity: agent
  shows:
  - Agent name
  - Availability
- entity: saved-reply
  shows:
  - Title
  - Message
  - Actions
entryPoints:
- helpdesk-web: /helpdesk/tickets/:ticketId
references:
- kind: code
  role: implementation
  target: desk/src/pages/ticket/TicketAgent.vue
- kind: code
  role: implementation
  target: desk/src/components/ticket-agent/TicketSidebar.vue
---

# Ticket

One ticket as agents work it: the conversation and comments, activity, details, assignees and SLA.
