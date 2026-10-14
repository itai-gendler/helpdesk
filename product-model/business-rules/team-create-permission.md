---
appliesTo:
- type: entity
  id: team
  effect: creates
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

# Agent Managers and System Managers create teams

Teams are configured in the administration area.
