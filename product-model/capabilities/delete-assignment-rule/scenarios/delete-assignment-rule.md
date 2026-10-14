---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager chooses Delete and confirms
  kind: actor
  actor: agent-manager
  entities:
  - entity: assignment-rule
    effect: reads
    facts:
    - Name
  contexts:
    main:
      place: helpdesk-web::administration::assignment-rules
- text: The Product deletes the Assignment rule
  kind: product
  actor: agent-manager
  entities:
  - entity: assignment-rule
    effect: removes
    from: Disabled
  contexts:
    main:
      place: helpdesk-web::administration::assignment-rules
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Assignment Rules/AssignmentRuleListItem.vue
- kind: code
  role: implementation
  target: helpdesk/extends/assignment_rule.py
---

# Delete an assignment rule

## Trigger

An Agent Manager deletes an Assignment rule.

## Outcome

The Assignment rule is gone.
