---
entities:
- entity: contact
  shows:
  - Name
  - Email
  - Image
  collects:
  - Name
  - Email
  - Phone
  - Image
entryPoints:
- helpdesk-web: /helpdesk/contacts
references:
- kind: code
  role: implementation
  target: desk/src/pages/contact/Contacts.vue
---

# Contacts

The contacts list, and adding a contact.
