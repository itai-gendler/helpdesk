---
appliesTo:
- type: entity
  id: invitation
  effect: creates
permits:
- actors:
  - system-manager
  - administrator
- actors:
  - agent-manager
  when:
  - fact: Role
    is-not: System Manager
references:
- kind: code
  role: implementation
  target: helpdesk/hooks.py
- kind: code
  role: implementation
  target: desk/src/components/Settings/InviteAgents.vue
---

# Managers invite staff, and only System Managers invite System Managers

Agent Managers invite agents, Agent Managers and customer contacts; System Managers may also invite System Managers.
