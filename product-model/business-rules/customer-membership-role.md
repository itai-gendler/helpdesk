---
appliesTo:
- type: entity
  id: customer-membership
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
  target: helpdesk/helpdesk/doctype/hd_customer/hd_customer.py
---

# Agent Managers and System Managers change a contact's role in a customer

The contact's portal roles follow the membership's role.
