---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager changes the rule and saves
  kind: actor
  actor: agent-manager
  entities:
  - entity: assignment-rule
    effect: reads
    facts:
    - Name
    - Description
    - Priority
    - Assignment condition
    - Unassignment condition
    - Assignment days
    - Routing
    - Assignees
    - Last assigned agent
  contexts:
    main:
      place: helpdesk-web::administration::assignment-rule
- text: The Product saves the Assignment rule
  kind: product
  actor: agent-manager
  entities:
  - entity: assignment-rule
    effect: changes
    facts:
    - Name
    - Description
    - Priority
    - Assignment condition
    - Unassignment condition
    - Assignment days
    - Routing
    - Assignees
  contexts:
    main:
      place: helpdesk-web::administration::assignment-rule
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Assignment Rules/AssignmentRuleView.vue
- kind: code
  role: implementation
  target: helpdesk/extends/assignment_rule.py
---

# Edit an assignment rule

## Trigger

An Agent Manager changes an Assignment rule.

## Outcome

Tickets saved from then on follow the changed rule.
