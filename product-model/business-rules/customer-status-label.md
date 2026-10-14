---
appliesTo:
- type: entity
  id: ticket
  effect: reads
  facts:
  - Status
  contexts:
  - place: helpdesk-web::customer-portal
references:
- kind: code
  role: implementation
  target: desk/src/pages/ticket/TicketCustomer.vue
- kind: code
  role: implementation
  target: helpdesk/setup/install.py
---

# Requesters see a status's customer label

A status set to show end users a different view appears to requesters under its customer label, such as Awaiting Response for Replied.
