---
appliesTo:
- type: entity
  id: agent
  effect: changes
  facts:
  - Active
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_agent/hd_agent.py
- kind: code
  role: implementation
  target: desk/src/components/Settings/Agents.vue
---

# Agent Managers and System Managers enable and disable agents

A disabled agent keeps their record and roles but has no agent access until a manager enables them again.
