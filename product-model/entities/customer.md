---
domain: customers
relations:
- entity: ticket
  verb: has
  cardinality: one-to-many
- entity: customer-membership
  verb: has
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_customer/hd_customer.py
- kind: code
  role: implementation
  target: helpdesk/api/customer.py
---

# Customer

A customer organization that tickets are raised for. Its contacts belong to it as members, each as a Customer or a Customer Manager; the primary contact is always a manager.

## Information kept

- **Customer name** — the organization's name
- **Domain** — the organization's web domain
- **Country** — where the organization is
- **Image** — the organization's logo
- **Primary contact** — the main contact, whose email and phone the customer shows
