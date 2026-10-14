---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager switches the Team on
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
- text: The Product enables the Team and its rotation
  kind: product
  actor: agent-manager
  entities:
  - entity: team
    effect: changes
    from: Disabled
    to: Enabled
    facts: []
  - entity: assignment-rule
    effect: changes
    from: Disabled
    to: Enabled
    facts: []
  contexts:
    main:
      place: helpdesk-web::administration::team
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_team/hd_team.py
---

# Enable a team

## Trigger

An Agent Manager switches a disabled Team on.

## Outcome

The Team and its rotation are enabled.
