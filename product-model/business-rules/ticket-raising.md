---
appliesTo:
- type: entity
  id: ticket
  effect: creates
permits:
- actors:
  - contact
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
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.json
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_settings/hd_settings.py
---

# Contacts and staff raise tickets

A contact raises tickets for themselves, by email or in the customer portal, and agents, managers and the Administrator raise them in the agent portal. A requester can attribute a ticket only to their own contact and to a customer they belong to. While Allow anyone to create tickets is on, people who are not signed in may create tickets too.
