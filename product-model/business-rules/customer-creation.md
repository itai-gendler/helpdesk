---
appliesTo:
- type: entity
  id: customer
  effect: creates
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/api/customer.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_customer/hd_customer.json
---

# Agent Managers and System Managers create customers

Agents without a manager role browse customers but do not add them.
