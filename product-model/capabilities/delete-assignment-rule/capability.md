---
availability:
- place: helpdesk-web::administration
domain: assignment-rules
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Assignment Rules/AssignmentRuleListItem.vue
- kind: code
  role: implementation
  target: helpdesk/extends/assignment_rule.py
---

# Delete assignment rule

Delete an assignment rule, as long as another ticket rule remains.
