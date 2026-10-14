---
availability:
- place: helpdesk-web::agent-portal
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_agent/hd_agent.py
- kind: code
  role: implementation
  target: desk/src/components/AvailabilityMenu.vue
---

# Change availability

Set one's own availability to an enabled agent status, such as Active, Away or Unavailable; assignment rules prefer available agents.
