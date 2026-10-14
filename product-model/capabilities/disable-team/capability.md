---
availability:
- place: helpdesk-web::administration
domain: teams
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_team/hd_team.py
- kind: code
  role: implementation
  target: desk/src/components/Settings/Teams/TeamEdit.vue
- kind: code
  role: implementation
  target: helpdesk/utils.py
---

# Disable team

Turn a team and its rotation off.
