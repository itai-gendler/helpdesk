---
appliesTo:
- type: entity
  id: agent
  effect: changes
  facts:
  - Availability
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
- self: true
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_agent/hd_agent.py
---

# An agent's availability is set by that agent or a manager

Only an enabled agent status may be chosen, and the change is shared live with everyone.
