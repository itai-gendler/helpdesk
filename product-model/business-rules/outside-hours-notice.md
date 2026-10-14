---
appliesTo:
- type: capability
  id: raise-ticket
- type: entity
  id: helpdesk-settings
  facts:
  - Outside working hours notice
  - Outside working hours message
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/api.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_settings/helpers.py
---

# A ticket raised outside working hours tells its requester when to expect a response

With the notice on, a ticket raised on a holiday or outside its policy's working hours shows its requester the configured message until the next working day begins or an agent replies.
