---
appliesTo:
- type: entity
  id: holiday-list
  effect: changes
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_holiday_list/hd_service_holiday_list.json
---

# Agent Managers and System Managers change holiday lists

The settings sections for holiday lists are part of the administration area; everyone else is refused.
