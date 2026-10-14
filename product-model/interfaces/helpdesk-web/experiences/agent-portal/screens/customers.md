---
entities:
- entity: customer
  shows:
  - Customer name
  - Domain
  - Image
  collects:
  - Customer name
  - Domain
  - Country
  - Image
- entity: contact
  collects:
  - Name
  - Email
  - Phone
entryPoints:
- helpdesk-web: /helpdesk/customers
references:
- kind: code
  role: implementation
  target: desk/src/pages/customer/Customers.vue
---

# Customers

The list of customer organizations.
