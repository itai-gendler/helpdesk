---
appliesTo:
- type: entity
  id: comment
  effect: changes
  facts:
  - Pinned
references:
- kind: code
  role: implementation
  target: helpdesk/extends/comment.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/api.py
---

# A ticket has at most five pinned comments

Pinning a sixth is refused, and comments copied by a merge arrive unpinned.
