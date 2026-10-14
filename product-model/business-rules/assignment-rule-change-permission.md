---
appliesTo:
- type: entity
  id: assignment-rule
  effect: changes
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
- unattended: true
references:
- kind: code
  role: implementation
  target: helpdesk/setup/install.py
- kind: code
  role: implementation
  target: helpdesk/extends/assignment_rule.py
---

# Agent Managers and System Managers change assignment rules

The settings sections for assignment rules are part of the administration area; everyone else is refused. Assigning a ticket automatically also records the rule's last assigned agent.
