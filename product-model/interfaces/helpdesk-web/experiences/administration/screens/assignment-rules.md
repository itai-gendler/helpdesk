---
entities:
- entity: assignment-rule
  shows:
  - Name
  - Description
  - Priority
  - Assignees
  collects:
  - Priority
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Assignment Rules/AssignmentRulesList.vue
---

# Assignment Rules

The assignment rules, their priority and whether each is enabled.
