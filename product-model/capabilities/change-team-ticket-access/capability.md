---
availability:
- place: helpdesk-web::administration
domain: teams
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Teams/TeamEdit.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Change team ticket access

Choose whether a team's members see only the team's tickets or every team's tickets while tickets are restricted by team.
