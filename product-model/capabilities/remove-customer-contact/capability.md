---
availability:
- place: helpdesk-web::agent-portal
domain: customers
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_customer/hd_customer.py
- kind: code
  role: implementation
  target: desk/src/components/customer/ContactCard.vue
---

# Remove customer contact

Take a contact out of a customer.
