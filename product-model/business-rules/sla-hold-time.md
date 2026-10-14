---
appliesTo:
- type: capability-scenario
  id: pause-ticket
- type: capability-scenario
  id: reopen-ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.py
---

# Paused time extends the resolution target

While a ticket is in a Paused-category status its hold time accrues in working time; on leaving the pause the hold time is added and the resolution target moves later by it. Time a reopened ticket spent resolved counts as hold time.
