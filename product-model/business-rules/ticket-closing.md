---
appliesTo:
- type: entity
  id: ticket
  effect: changes
  to: Closed
permits:
- actors:
  - agent
  - agent-manager
  - system-manager
  - administrator
- related:
  - verb: raises
    entity: contact
  when:
  - fact: Feedback
    absent: true
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
- unattended: true
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Requesters, their Customer Managers, staff and the daily auto-close close a ticket

A requester closes their own ticket while it is not yet Closed or rated; a Customer Manager closes their customer's tickets; staff close any ticket they may change; the Product closes stale tickets on its own.
