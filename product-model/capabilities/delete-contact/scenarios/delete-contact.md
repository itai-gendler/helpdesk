---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent Manager chooses Delete and keeps the tickets
  kind: actor
  actor: agent-manager
  entities:
  - entity: contact
    effect: reads
    facts:
    - Name
  - entity: ticket
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::contact
- text: The Product removes the Contact from its Customers and deletes the Contact
  kind: product
  actor: agent-manager
  entities:
  - entity: contact
    effect: removes
  - entity: customer-membership
    effect: removes
    with: contact
  - entity: customer
    effect: reads
    facts: []
  - entity: ticket
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::contact
references:
- kind: code
  role: implementation
  target: helpdesk/api/contact.py
---

# Delete a contact and keep their tickets

## Trigger

An Agent Manager deletes a Contact and keeps their tickets.

## Outcome

The Contact is gone, no longer belongs to any Customer, and their Tickets remain.

## Edge cases

- Choosing to delete the tickets too removes every ticket of the contact, and needs permission to delete tickets.
