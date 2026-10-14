---
appliesTo:
- type: capability-scenario
  id: reply-to-closed-ticket-refused
- type: capability
  id: close-ticket
- type: capability
  id: edit-ticket-details
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
---

# Requesters cannot change a Closed or rated ticket

Once a ticket is Closed or carries a rating, its requester can no longer reply in the portal, change fields or rate it again; agents still can.
