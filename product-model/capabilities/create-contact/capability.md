---
availability:
- place: helpdesk-web::agent-portal
domain: contacts
references:
- kind: code
  role: implementation
  target: helpdesk/api/contact.py
- kind: code
  role: implementation
  target: desk/src/pages/contact/Contacts.vue
---

# Create contact

Add a contact, optionally inviting them to the customer portal.
