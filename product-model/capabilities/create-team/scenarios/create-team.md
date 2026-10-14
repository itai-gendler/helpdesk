---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager gives a name, picks members and sets whether it is enabled
  kind: actor
  actor: agent-manager
  entities: []
  contexts:
    main:
      place: helpdesk-web::administration::teams
- text: The Product creates the Team and its support rotation Assignment rule
  kind: product
  actor: agent-manager
  entities:
  - entity: team
    effect: creates
    to: Enabled
    facts:
    - Name
    - Members
    - Ticket access
  - entity: assignment-rule
    effect: creates
    to: Enabled
    facts:
    - Name
    - Assignment condition
    - Unassignment condition
    - Assignment days
    - Assignees
    - Priority
    with: team
  contexts:
    main:
      place: helpdesk-web::administration::teams
- text: The new Team's page opens
  kind: condition
  entities:
  - entity: team
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::administration::team
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_team/hd_team.py
---

# Create a team

## Trigger

An Agent Manager creates a team with its first members.

## Outcome

The Team exists with a support rotation that assigns the team's open tickets to its members, and its page opens.

## Edge cases

- A team created disabled gets a disabled rotation.
