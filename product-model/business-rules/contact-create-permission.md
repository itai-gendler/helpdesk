---
appliesTo:
- type: entity
  id: contact
  effect: creates
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

# Agent Managers and System Managers create contacts

Agents see contacts and their tickets.
