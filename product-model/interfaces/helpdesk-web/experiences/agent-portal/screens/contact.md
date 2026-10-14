---
entities:
- entity: contact
  shows:
  - Name
  - Email
  - Phone
  - Image
  - Portal account
  collects:
  - Name
  - Email
  - Phone
  - Image
- entity: invitation
  shows:
  - Status
- entity: ticket
  shows:
  - Subject
  - Status
  - Rating
  - Feedback comment
entryPoints:
- helpdesk-web: /helpdesk/contacts/:id
references:
- kind: code
  role: implementation
  target: desk/src/pages/contact/Contact.vue
---

# Contact

One contact: details, customers, portal invitation, tickets and feedback.
