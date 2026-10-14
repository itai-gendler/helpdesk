---
availability:
- place: helpdesk-web::agent-portal
domain: customers
references:
- kind: code
  role: implementation
  target: helpdesk/api/customer.py
- kind: code
  role: implementation
  target: desk/src/components/customer/NewCustomerDialog.vue
---

# Create customer

Add a customer organization, optionally with a primary contact who is invited to the portal.
