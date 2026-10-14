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

# Edit contact

Change a contact's name, email addresses, phone numbers and picture.
