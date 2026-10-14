---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager switches the rule off
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
- text: The Product disables the Assignment rule
  kind: product
  actor: agent-manager
  entities:
  - entity: assignment-rule
    effect: changes
    from: Enabled
    to: Disabled
    facts: []
  contexts:
    main:
      place: helpdesk-web::administration::assignment-rules
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Assignment Rules/AssignmentRuleListItem.vue
---

# Disable an assignment rule

## Trigger

An Agent Manager switches an Assignment rule off.

## Outcome

The rule no longer assigns tickets.
