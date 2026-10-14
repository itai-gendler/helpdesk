---
appliesTo:
- type: entity
  id: ticket
  effect: removes
permits:
- actors:
  - administrator
references:
- kind: code
  role: implementation
  target: helpdesk/api/ticket.py
---

# Only the Administrator deletes a ticket

Deleting a ticket is refused to everyone but the site's built-in Administrator account, System Managers included.
