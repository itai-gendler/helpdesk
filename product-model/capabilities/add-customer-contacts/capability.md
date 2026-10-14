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
  target: desk/src/components/customer/InviteContactDialog.vue
---

# Add customer contacts

Add contacts to a customer by contact or email address, as Customers or Customer Managers; people without a portal account are invited by email.
