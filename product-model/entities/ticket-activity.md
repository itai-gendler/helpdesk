---
domain: tickets
references:
- kind: code
  role: implementation
  target: helpdesk/patches/migrate_ticket_activities_to_info_comments.py
- kind: code
  role: implementation
  target: desk/src/components/ticket-agent/TicketActivityPanel.vue
---

# Ticket activity

The activity agents read on a ticket: status and field changes, assignments, splits, automatic closing and other recorded events.

## Information kept

- **Actor** — who caused the change, or the Product
- **Change** — what changed
- **Time** — when it changed
