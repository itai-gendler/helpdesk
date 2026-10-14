---
entities:
- entity: customer
  shows:
  - Customer name
  - Domain
  - Country
  - Image
  - Primary contact
- entity: customer-membership
  shows:
  - Role
  collects:
  - Role
- entity: contact
  shows:
  - Name
  - Email
  - Phone
  collects:
  - Email
- entity: ticket
  shows:
  - Subject
  - Status
  - Priority
  - First response due
  - Resolution due
  - Assigned agents
entryPoints:
- helpdesk-web: /helpdesk/customers/:id
references:
- kind: code
  role: implementation
  target: desk/src/pages/customer/Customer.vue
- kind: code
  role: implementation
  target: desk/src/components/customer/ContactCard.vue
---

# Customer

One customer: its details, its contacts and their roles, and its tickets.
