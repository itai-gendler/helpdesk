---
domain: tickets
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/overrides/email_account.py
---

# Reply

One message in a ticket's conversation: an email or portal message from the requester's side, or an agent's reply, which is emailed to the requester unless email is switched off.

## Information kept

- **Message** — the message body
- **Sender** — who sent it
- **Direction** — Received from the requester's side or Sent by an agent
- **To** — the recipients of an agent's reply
- **CC** — copied recipients
- **BCC** — blind-copied recipients
- **Attachments** — files sent with the message, also attached to the ticket
- **Sent at** — when it was sent
