---
availability:
- place: helpdesk-web::agent-portal
domain: tickets
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/extends/comment.py
---

# Add comment

Leave an internal note on a ticket, optionally mentioning agents. Notes and their files stay out of the requester's sight.
