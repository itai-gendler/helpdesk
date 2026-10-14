---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent Manager chooses Delete and keeps the tickets
  kind: actor
  actor: agent-manager
  entities:
  - entity: customer
    effect: reads
    facts:
    - Customer name
  - entity: ticket
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::customer
- text: The Product deletes the Customer and clears it from its Tickets
  kind: product
  actor: agent-manager
  entities:
  - entity: customer
    effect: removes
  - entity: customer-membership
    effect: removes
    with: customer
  - entity: ticket
    effect: changes
    facts:
    - Customer
  contexts:
    main:
      place: helpdesk-web::agent-portal::customer
references:
- kind: code
  role: implementation
  target: helpdesk/api/customer.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_customer/hd_customer.py
---

# Delete a customer and keep its tickets

## Trigger

An Agent Manager deletes a Customer and keeps its tickets.

## Outcome

The Customer is gone; its Tickets remain without a customer and its pending invitations no longer name it.

## Edge cases

- Choosing to delete the tickets too removes every ticket of the customer, and needs permission to delete tickets.
