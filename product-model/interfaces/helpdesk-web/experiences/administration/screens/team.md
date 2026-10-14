---
entities:
- entity: team
  shows:
  - Name
  - Members
  - Ticket access
  collects:
  - Name
  - Members
  - Ticket access
- entity: agent
  shows:
  - Agent name
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Teams/TeamEdit.vue
---

# Team

One team: its members, ticket access and whether it is enabled.
