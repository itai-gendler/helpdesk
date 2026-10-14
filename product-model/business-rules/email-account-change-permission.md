---
appliesTo:
- type: entity
  id: email-account
  effect: changes
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/api/settings/email.py
- kind: code
  role: implementation
  target: helpdesk/setup/install.py
---

# Agent Managers and System Managers change email accounts

Email Accounts is part of the administration area.
