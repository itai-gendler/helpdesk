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
  target: desk/src/components/Settings/Assignment Rules/AssignmentRuleListItem.vue
- kind: code
  role: implementation
  target: helpdesk/extends/assignment_rule.py
---

# Edit assignment rule

Change an assignment rule's conditions, schedule, routing, priority and assignees.
