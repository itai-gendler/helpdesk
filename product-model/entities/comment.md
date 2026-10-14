---
domain: tickets
references:
- kind: code
  role: implementation
  target: helpdesk/extends/comment.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Comment

An internal note an agent leaves on a ticket. Comments are for agents only; requesters never see them.

## Information kept

- **Content** — the note, which may mention agents
- **Author** — the agent who wrote it
- **Mentions** — the agents mentioned, who are notified
- **Attachments** — files added with the note, readable only where the comment is
- **Pinned** — whether the comment is pinned to the top of the ticket
- **Reactions** — the emoji reactions agents left, one per agent
