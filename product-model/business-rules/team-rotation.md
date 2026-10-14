---
appliesTo:
- type: capability
  id: create-team
- type: capability
  id: rename-team
- type: capability
  id: add-team-member
- type: capability
  id: remove-team-member
- type: capability-scenario
  id: assign-ticket-by-rule
- type: capability-scenario
  id: unassign-ticket-by-rule
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_team/hd_team.py
---

# A team's rotation assigns its open tickets to its members

Each team keeps one assignment rule whose assignees are the team's members. It assigns tickets whose status is Open and whose team is that team, and unassigns them when they move to another team; renaming, enabling, disabling or deleting the team does the same to its rotation.
