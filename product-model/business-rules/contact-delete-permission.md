---
appliesTo:
- type: entity
  id: contact
  effect: removes
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/api/contact.py
- kind: code
  role: implementation
  target: helpdesk/setup/install.py
---

# Agent Managers and System Managers delete contacts

Agents see contacts and their tickets.
