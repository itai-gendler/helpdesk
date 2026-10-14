---
appliesTo:
- type: entity
  id: reply
  effect: creates
  contexts:
  - place: helpdesk-web::agent-portal
permits:
- actors:
  - agent
  - agent-manager
  - system-manager
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/api/ticket.py
---

# Only agents reply as the support team

Replies sent from the agent portal, singly or to several selected tickets, need agent access and permission to change each ticket.
