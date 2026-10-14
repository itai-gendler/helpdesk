---
entities:
- entity: ticket
  shows:
  - Status
  - Team
  - Ticket type
  - Priority
  - SLA status
  - Rating
  - Raised via portal
entryPoints:
- helpdesk-web: /helpdesk/dashboard
references:
- kind: code
  role: implementation
  target: desk/src/pages/dashboard/Dashboard.vue
---

# Dashboard

Ticket and SLA figures for a period.
