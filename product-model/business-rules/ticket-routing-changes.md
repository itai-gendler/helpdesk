---
appliesTo:
- type: entity
  id: ticket
  effect: changes
  facts:
  - Subject
  - Priority
  - Ticket type
  - Team
  - Customer
permits:
- actors:
  - agent
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
- kind: code
  role: implementation
  target: helpdesk/consts.py
---

# Only staff change a ticket's subject, priority, type, team or customer

Requesters cannot change these after raising the ticket; the change is refused, not silently dropped.
