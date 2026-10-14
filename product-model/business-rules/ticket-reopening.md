---
appliesTo:
- type: entity
  id: ticket
  effect: changes
  to: Open
permits:
- actors:
  - agent
  - agent-manager
  - system-manager
  - administrator
- related:
  - verb: raises
    entity: contact
- related:
  - verb: has
    entity: customer
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
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
---

# Requester replies and staff reopen a ticket

A requester's reply moves a ticket back to its reopen status; staff reopen by choosing an Open-category status.
