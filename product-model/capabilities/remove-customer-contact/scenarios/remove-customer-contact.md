---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent Manager chooses to remove the member and confirms
  kind: actor
  actor: agent-manager
  entities:
  - entity: customer-membership
    effect: reads
    facts:
    - Role
  contexts:
    main:
      place: helpdesk-web::agent-portal::customer
- text: The Product removes the membership and clears the primary contact if it was this Contact
  kind: product
  actor: agent-manager
  entities:
  - entity: customer-membership
    effect: removes
  - entity: customer
    effect: changes
    facts:
    - Primary contact
  - entity: contact
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::customer
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_customer/hd_customer.py
- kind: code
  role: implementation
  target: helpdesk/api/contact.py
---

# Remove a contact from a customer

## Trigger

An Agent Manager removes a Contact from a Customer.

## Outcome

The Contact no longer belongs to the Customer; if it was the primary contact, the Customer has none.
