---
appliesTo:
- type: entity
  id: customer-membership
  effect: creates
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_customer/hd_customer.py
---

# Only Agent Managers and System Managers add contacts to a customer

Adding contacts, directly or by invitation, is refused to everyone else.
