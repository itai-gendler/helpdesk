---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager switches the Team off
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
- text: The Product disables the Team and its rotation
  kind: product
  actor: agent-manager
  entities:
  - entity: team
    effect: changes
    from: Enabled
    to: Disabled
    facts: []
  - entity: assignment-rule
    effect: changes
    from: Enabled
    to: Disabled
    facts: []
  contexts:
    main:
      place: helpdesk-web::administration::team
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_team/hd_team.py
---

# Disable a team

## Trigger

An Agent Manager switches a Team off.

## Outcome

The Team and its rotation are disabled and the Team grants no ticket access.
