---
appliesTo:
- type: entity
  id: assignment-rule
  effect: creates
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

# Agent Managers and System Managers create assignment rules

The settings sections for assignment rules are part of the administration area; everyone else is refused.
