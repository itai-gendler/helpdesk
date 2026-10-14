---
appliesTo:
- type: entity
  id: customer-membership
  effect: removes
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_customer/hd_customer.py
- kind: code
  role: implementation
  target: helpdesk/api/contact.py
---

# Agent Managers and System Managers remove contacts from a customer

Removing the primary contact also clears the customer's primary contact.
