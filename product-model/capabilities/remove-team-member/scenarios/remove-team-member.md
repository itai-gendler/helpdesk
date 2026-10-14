---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager removes an Agent
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
- text: The Product removes the member from the Team and its rotation's Assignees
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

# Remove a member from a team

## Trigger

An Agent Manager removes an Agent from a Team.

## Outcome

The Agent is no longer a member or in the Team's rotation.
