---
appliesTo:
- type: entity
  id: invitation
  effect: changes
  facts:
  - Status
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/setup/install.py
---

# Agent Managers and System Managers cancel invitations

A cancelled invitation can no longer be accepted.
