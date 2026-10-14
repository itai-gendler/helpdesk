---
appliesTo:
- type: entity
  id: ticket
  effect: changes
  facts:
  - SLA clock start
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# SLA targets count from when the policy attaches

The clock start is set once, when a policy first attaches, which may be later than when the ticket was raised; losing and regaining a policy keeps the original start.
