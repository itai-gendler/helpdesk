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

# Only one SLA policy is the default

Making a policy the default takes the default away from the previous one.
