---
appliesTo:
- type: entity
  id: ticket
  effect: changes
  facts:
  - Assigned agents
permits:
- actors:
  - agent
  - agent-manager
  - system-manager
  - administrator
- unattended: true
references:
- kind: code
  role: implementation
  target: helpdesk/api/ticket.py
- kind: code
  role: implementation
  target: helpdesk/api/doc.py
- kind: code
  role: implementation
  target: helpdesk/overrides/assignment_rule.py
---

# Staff and assignment rules assign tickets

Agents assign and unassign agents on tickets they may change; enabled assignment rules do so automatically as tickets are saved. Only agents can be assigned.
