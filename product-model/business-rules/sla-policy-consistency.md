---
appliesTo:
- type: capability
  id: create-sla-policy
- type: capability
  id: edit-sla-policy
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.py
---

# An SLA policy's targets and working hours hold together

Every priority has a first response time, not longer than its resolution time while resolution targets apply; priorities and workdays are not repeated; exactly one priority is the default; each workday starts before it ends.
