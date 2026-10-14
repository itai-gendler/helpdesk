---
appliesTo:
- type: capability
  id: raise-ticket
- type: capability
  id: reply-to-ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# New tickets start, and requester replies reopen, in the policy's statuses

A new ticket starts in its SLA policy's default ticket status, and a requester's reply after an agent has answered moves it to the policy's reopen status; where the policy names none, the Helpdesk settings' statuses apply.
