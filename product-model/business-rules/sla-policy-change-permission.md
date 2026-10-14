---
appliesTo:
- type: entity
  id: sla-policy
  effect: changes
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.json
---

# Agent Managers and System Managers change SLA policies

The settings sections for SLA policies are part of the administration area; everyone else is refused.
