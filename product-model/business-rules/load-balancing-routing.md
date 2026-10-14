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

# Assign by workload picks the least-loaded assignee

The rule hands each ticket to the eligible assignee with the fewest open assignments.
