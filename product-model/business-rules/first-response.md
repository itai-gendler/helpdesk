---
appliesTo:
- type: entity
  id: ticket
  effect: changes
  facts:
  - First responded on
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.py
---

# The first agent reply or the first move off Open is the first response

A ticket's first response is set once: by the first reply an agent sends, or — if none came first — when an agent first moves the ticket from Open to a Paused or Resolved status.
