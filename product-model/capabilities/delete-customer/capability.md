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
  target: helpdesk/helpdesk/doctype/hd_customer/hd_customer.py
---

# Delete customer

Delete a customer organization, keeping its tickets without a customer or deleting them too.
