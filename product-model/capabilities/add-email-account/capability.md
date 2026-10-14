---
availability:
- place: helpdesk-web::administration
domain: email-accounts
references:
- kind: code
  role: implementation
  target: helpdesk/api/settings/email.py
- kind: code
  role: implementation
  target: desk/src/components/Settings/EmailAdd.vue
---

# Add email account

Connect a mailbox from Gmail, Outlook, Frappe Mail or a custom server, for incoming tickets, outgoing replies or both.
