---
availability:
- place: helpdesk-web::administration
domain: sla-policies
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Sla/SlaPolicyView.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.py
---

# Edit SLA policy

Change an SLA policy's details, conditions, targets, working hours, holiday list and statuses.
