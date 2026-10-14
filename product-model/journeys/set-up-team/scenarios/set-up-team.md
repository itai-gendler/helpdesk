---
kind: primary
result: achieved
routes:
  main: Administration
steps:
- text: The Agent Manager creates the Team
  kind: actor
  actor: agent-manager
  entities:
  - entity: team
    effect: creates
    to: Enabled
    facts:
    - Name
    - Members
    - Ticket access
  contexts:
    main:
      place: helpdesk-web::administration::teams
  capability: create-team
- text: The Product opens the new Team's page
  kind: product
  actor: agent-manager
  entities:
  - entity: team
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::administration::team
  capability: create-team
- text: The Agent Manager adds a member to the Team
  kind: actor
  actor: agent-manager
  entities:
  - entity: team
    effect: changes
    facts:
    - Members
  contexts:
    main:
      place: helpdesk-web::administration::team
  capability: add-team-member
---

# Create a team and add a member

## Trigger

An Agent Manager creates a team.

## Outcome

The Agent Manager is on the new team's page and has added a member.
