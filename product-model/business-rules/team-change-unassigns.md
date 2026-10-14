---
appliesTo:
- type: capability-scenario
  id: edit-ticket-details
- type: entity
  id: ticket
  effect: changes
  facts:
  - Team
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Moving an open ticket to another team drops an assignee outside it

When an open ticket's team changes and its assignee is not a member of the new team, the assignment is cleared if the new team's rotation is enabled and has assignees.
