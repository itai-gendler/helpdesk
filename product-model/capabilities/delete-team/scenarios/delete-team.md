---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager chooses Delete and confirms
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
- text: The Product deletes the Team and its rotation Assignment rule
  kind: product
  actor: agent-manager
  entities:
  - entity: team
    effect: removes
    from: Enabled
  - entity: assignment-rule
    effect: removes
    from: Enabled
    with: team
  contexts:
    main:
      place: helpdesk-web::administration::team
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_team/hd_team.py
---

# Delete a team

## Trigger

An Agent Manager deletes a Team.

## Outcome

The Team and its rotation are gone.
