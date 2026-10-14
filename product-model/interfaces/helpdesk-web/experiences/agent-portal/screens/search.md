---
entities:
- entity: ticket
  shows:
  - Subject
  - Status
- entity: reply
  shows:
  - Message
- entity: comment
  shows:
  - Content
entryPoints:
- helpdesk-web: /helpdesk/search
references:
- kind: code
  role: implementation
  target: desk/src/pages/SearchAgent.vue
---

# Search

Searching tickets, their replies and comments.
