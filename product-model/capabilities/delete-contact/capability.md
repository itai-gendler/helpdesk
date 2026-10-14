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
  target: desk/src/pages/contact/Contact.vue
---

# Delete contact

Delete a contact, keeping their tickets without a contact or deleting them too.
