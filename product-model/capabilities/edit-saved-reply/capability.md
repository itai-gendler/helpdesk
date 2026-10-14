---
availability:
- place: helpdesk-web::agent-portal
domain: saved-replies
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/SavedReplies/SavedReplyView.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_saved_reply/hd_saved_reply.py
---

# Edit saved reply

Change a saved reply's text, scope, teams and actions.
