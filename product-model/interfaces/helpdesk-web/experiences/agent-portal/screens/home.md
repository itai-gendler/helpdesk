---
entities:
- entity: ticket
  shows:
  - Subject
  - Status
  - Assigned agents
  - First response time
  - Resolution time
  - Rating
entryPoints:
- helpdesk-web: /helpdesk/home
references:
- kind: code
  role: implementation
  target: desk/src/pages/home/Home.vue
---

# Home

An agent's own tickets and figures.
