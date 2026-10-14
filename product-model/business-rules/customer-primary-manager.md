---
appliesTo:
- type: entity
  id: customer
  effect: changes
  facts:
  - Primary contact
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_customer/hd_customer.py
---

# A customer's primary contact is always one of its Customer Managers

Setting a primary contact adds them as a manager, and removing the primary contact from the customer clears the primary contact.
