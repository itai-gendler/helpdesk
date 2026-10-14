---
availability:
- place: helpdesk-web::administration
domain: assignment-rules
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Assignment Rules/AssignmentRuleView.vue
- kind: code
  role: implementation
  target: helpdesk/extends/assignment_rule.py
---

# Create assignment rule

Create an assignment rule with its conditions, schedule, routing and assignees.
