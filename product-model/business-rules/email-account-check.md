---
appliesTo:
- type: capability
  id: add-email-account
- type: entity
  id: email-account
  effect: creates
references:
- kind: code
  role: implementation
  target: helpdesk/api/settings/email.py
---

# A mailbox is saved only when its incoming server accepts the credentials

Every connected mailbox pulls its inbox into tickets.
