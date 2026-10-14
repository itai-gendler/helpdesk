---
appliesTo:
- type: entity
  id: team
  effect: changes
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_team/hd_team.py
- kind: code
  role: implementation
  target: desk/src/components/Settings/settingsModal.ts
---

# Agent Managers and System Managers change teams

Teams are configured in the administration area.
