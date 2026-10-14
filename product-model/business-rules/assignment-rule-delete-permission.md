---
appliesTo:
- type: entity
  id: assignment-rule
  effect: removes
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/setup/install.py
- kind: code
  role: implementation
  target: helpdesk/extends/assignment_rule.py
---

# Agent Managers and System Managers delete assignment rules

The settings sections for assignment rules are part of the administration area; everyone else is refused.
