---
domain: email-accounts
references:
- kind: code
  role: implementation
  target: helpdesk/api/settings/email.py
- kind: code
  role: implementation
  target: desk/src/components/Settings/emailConfig.ts
---

# Email account

A mailbox connected to the Helpdesk: incoming mail raises and updates tickets, outgoing mail carries agents' replies and notifications.

## Information kept

- **Account name** — the account's name
- **Email address** — the mailbox address
- **Service** — Gmail, Outlook, Frappe Mail or a custom server
- **Incoming** — whether mail is pulled into tickets
- **Outgoing** — whether mail is sent through it
- **Default incoming** — whether it is the default incoming account
- **Default outgoing** — whether it is the default outgoing account
- **Credentials** — the password or API key, and for a custom server its incoming and outgoing servers
