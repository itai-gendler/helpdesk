---
appliesTo:
- type: entity
  id: agent
  effect: changes
  facts:
  - Role
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Agents.vue
---

# Agent Managers and System Managers change an agent's role

The Agents section offers Manager and Agent.
