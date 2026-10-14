---
availability:
- place: helpdesk-web::agent-portal
domain: tickets
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/api.py
- kind: code
  role: implementation
  target: desk/src/components/ticket/TicketMergeModal.vue
---

# Merge ticket

Merge an open or paused ticket into another ticket: the conversation, comments and files are copied to the target and the source is closed as merged.
