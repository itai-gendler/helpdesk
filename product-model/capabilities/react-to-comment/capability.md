---
availability:
- place: helpdesk-web::agent-portal
domain: tickets
references:
- kind: code
  role: implementation
  target: helpdesk/api/comment.py
- kind: code
  role: implementation
  target: desk/src/components/ticket-agent/timeline/TimelineReactions.vue
---

# React to comment

React to a ticket comment with one of the preset emojis, while comment reactions are enabled.
