---
entities:
- entity: email-account
  shows:
  - Account name
  - Email address
  - Service
  - Incoming
  - Outgoing
  - Default incoming
  - Default outgoing
  collects:
  - Account name
  - Email address
  - Service
  - Incoming
  - Outgoing
  - Default incoming
  - Default outgoing
  - Credentials
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/EmailAdd.vue
- kind: code
  role: implementation
  target: desk/src/components/Settings/EmailEdit.vue
---

# Email account

Connecting or editing one mailbox.
