---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager switches the rule on
  kind: actor
  actor: agent-manager
  entities:
  - entity: assignment-rule
    effect: reads
    facts:
    - Name
    - Assignees
  contexts:
    main:
      place: helpdesk-web::administration::assignment-rules
- text: The Product enables the Assignment rule
  kind: product
  actor: agent-manager
  entities:
  - entity: assignment-rule
    effect: changes
    from: Disabled
    to: Enabled
    facts: []
  contexts:
    main:
      place: helpdesk-web::administration::assignment-rules
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Assignment Rules/AssignmentRuleListItem.vue
---

# Enable an assignment rule

## Trigger

An Agent Manager switches a disabled Assignment rule on.

## Outcome

The rule assigns tickets again.

## Edge cases

- A rule with no assignees cannot be switched on.
