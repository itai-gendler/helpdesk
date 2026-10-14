---
appliesTo:
- type: entity
  id: ticket
  effect: changes
  to: Paused
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
---

# Only staff pause a ticket

Paused statuses mean the support team has answered; a requester cannot set one.
