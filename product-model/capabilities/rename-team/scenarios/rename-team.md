---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager enters the new name
  kind: actor
  actor: agent-manager
  entities:
  - entity: team
    effect: reads
    facts:
    - Name
  contexts:
    main:
      place: helpdesk-web::administration::team
- text: The Product renames the Team and updates its rotation's conditions
  kind: product
  actor: agent-manager
  entities:
  - entity: team
    effect: changes
    facts:
    - Name
  - entity: assignment-rule
    effect: changes
    facts:
    - Assignment condition
    - Unassignment condition
  contexts:
    main:
      place: helpdesk-web::administration::team
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_team/hd_team.py
---

# Rename a team

## Trigger

An Agent Manager renames a Team.

## Outcome

The Team has its new name and its rotation now matches tickets of the new name.
