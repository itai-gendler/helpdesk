---
entities:
- entity: assignment-rule
  shows:
  - Name
  - Description
  - Priority
  - Assignment condition
  - Unassignment condition
  - Assignment days
  - Routing
  - Assignees
  - Last assigned agent
  collects:
  - Name
  - Description
  - Priority
  - Assignment condition
  - Unassignment condition
  - Assignment days
  - Routing
  - Assignees
- entity: agent
  shows:
  - Agent name
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Assignment Rules/AssignmentRuleView.vue
---

# Assignment rule

Creating or editing one assignment rule.
