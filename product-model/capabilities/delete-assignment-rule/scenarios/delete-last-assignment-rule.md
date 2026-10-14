---
kind: validation
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
- text: The Product refuses because it is the last Assignment rule left
  kind: condition
  actor: agent-manager
  entities:
  - entity: assignment-rule
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::administration::assignment-rules
references:
- kind: code
  role: implementation
  target: helpdesk/extends/assignment_rule.py
---

# Refuse deleting the last assignment rule

## Trigger

An Agent Manager deletes the only remaining Assignment rule for tickets.

## Outcome

The rule stays and the Agent Manager is told at least one must remain.
