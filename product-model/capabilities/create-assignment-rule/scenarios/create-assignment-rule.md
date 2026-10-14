---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager enters the name, priority, conditions, active days, routing and assignees
  kind: actor
  actor: agent-manager
  entities:
  - entity: agent
    effect: reads
    facts:
    - Agent name
  contexts:
    main:
      place: helpdesk-web::administration::assignment-rule
- text: The Product creates the Assignment rule
  kind: product
  actor: agent-manager
  entities:
  - entity: assignment-rule
    effect: creates
    to: Enabled
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

# Create an assignment rule

## Trigger

An Agent Manager sets up automatic assignment for some tickets.

## Outcome

The Assignment rule exists and assigns matching tickets as they are saved.

## Edge cases

- Conditions that are not valid are refused.
- An assignee outside the rule's team, for a team rotation, draws a warning.
