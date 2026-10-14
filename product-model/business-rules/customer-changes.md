---
appliesTo:
- type: entity
  id: customer
  effect: changes
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
- related:
  - verb: has
    entity: customer-membership
  - verb: holds
    entity: contact
  when:
  - entity: customer-membership
    fact: Role
    is: Customer Manager
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_customer/hd_customer.py
---

# Agent Managers, System Managers and the customer's own managers change a customer

Members of a customer may read it; only its Customer Managers among them may change it.
