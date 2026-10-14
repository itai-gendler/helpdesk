---
appliesTo:
- type: entity
  id: ticket
  effect: changes
  facts:
  - First response due
  - Resolution due
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.py
---

# SLA targets count only working hours outside holidays

First response and resolution targets are counted forward from the clock start through the policy's working hours on its working days, skipping the days of its holiday list; elapsed response and resolution times are measured the same way.
