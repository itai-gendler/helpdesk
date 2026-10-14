---
availability:
- place: helpdesk-web::administration
domain: teams
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Teams/RenameTeamModal.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_team/hd_team.py
---

# Rename team

Give a team a new name; its rotation follows the new name.
