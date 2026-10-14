---
type: messaging
actors:
- contact
references:
- kind: code
  role: implementation
  target: helpdesk/overrides/email_account.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.json
---

# Support email

The support mailbox a site's email account pulls into the Helpdesk. A new email to it raises a ticket; a reply in a ticket's email thread joins that ticket's conversation. Bounces and machine-generated mail are set aside instead of becoming tickets.
