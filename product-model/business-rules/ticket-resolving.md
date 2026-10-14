---
appliesTo:
- type: entity
  id: ticket
  effect: changes
  to: Resolved
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

# Only staff resolve a ticket

Resolving stops the SLA clock and is the support team's call; requesters may only close.
