---
availability:
- place: helpdesk-web::agent-portal
domain: tickets
references:
- kind: code
  role: implementation
  target: helpdesk/extends/comment.py
- kind: code
  role: implementation
  target: desk/src/components/ticket-agent/timeline/TimelineCommentRow.vue
---

# Edit comment

Change the text of a comment on a ticket.
