---
appliesTo:
- type: capability-scenario
  id: assign-ticket-by-rule
- type: entity
  id: assignment-rule
  effect: changes
  facts:
  - Last assigned agent
references:
- kind: code
  role: implementation
  target: helpdesk/overrides/assignment_rule.py
- kind: code
  role: implementation
  target: desk/src/components/Settings/Assignment Rules/AssigneeRules.vue
---

# Auto-rotate assigns the next assignee after the last one

The rule hands each ticket to the assignee after the one it assigned last, cycling through its eligible assignees.
