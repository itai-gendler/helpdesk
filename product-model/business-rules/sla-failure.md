---
appliesTo:
- type: entity
  id: ticket
  effect: changes
  facts:
  - SLA status
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# A missed target fails the agreement

A ticket whose first response or, where resolution targets apply, resolution comes after its due time — or is still missing when the due time passes — has SLA status Failed, and a failed status is kept even if the ticket later loses its policy.
