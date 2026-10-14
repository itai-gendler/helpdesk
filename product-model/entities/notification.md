---
references:
- kind: code
  role: implementation
  target: helpdesk/notifications.py
- kind: code
  role: implementation
  target: desk/src/components/notifications/Notifications.vue
---

# Notification

An in-app notification for an agent: being assigned a ticket, being mentioned in a comment, a reaction to their comment, or a ticket of theirs being reopened.

## Information kept

- **Kind** — Assignment, Mention, Reaction or Ticket Reopened
- **Subject** — what happened and on which ticket
- **From** — who caused it
- **Read** — whether the agent has read it
