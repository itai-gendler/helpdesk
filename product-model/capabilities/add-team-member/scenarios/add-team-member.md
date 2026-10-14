---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager picks an Agent to add
  kind: actor
  actor: agent-manager
  entities:
  - entity: team
    effect: reads
    facts:
    - Members
  - entity: agent
    effect: reads
    facts:
    - Agent name
  contexts:
    main:
      place: helpdesk-web::administration::team
- text: The Product adds the member to the Team and its rotation's Assignees
  kind: product
  actor: agent-manager
  entities:
  - entity: team
    effect: changes
    facts:
    - Members
  - entity: assignment-rule
    effect: changes
    facts:
    - Assignees
  contexts:
    main:
      place: helpdesk-web::administration::team
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_team/hd_team.py
---

# Add a member to a team

## Trigger

An Agent Manager adds an Agent to a Team.

## Outcome

The Agent is a member and is in the Team's rotation.
