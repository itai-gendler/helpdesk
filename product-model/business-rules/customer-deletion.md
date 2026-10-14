---
appliesTo:
- type: entity
  id: customer
  effect: removes
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
  target: helpdesk/api/customer.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_customer/hd_customer.py
---

# Agent Managers, System Managers and the customer's own managers delete a customer

Deleting the customer's tickets with it also needs permission to delete tickets; otherwise its tickets are kept without a customer.
