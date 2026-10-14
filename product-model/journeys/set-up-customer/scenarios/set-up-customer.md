---
kind: primary
result: achieved
routes:
  main: Agent portal
steps:
- text: The Agent Manager creates the Customer
  kind: actor
  actor: agent-manager
  entities:
  - entity: customer
    effect: creates
    facts:
    - Customer name
    - Domain
    - Country
    - Image
    - Primary contact
  contexts:
    main:
      place: helpdesk-web::agent-portal::customers
  capability: create-customer
- text: The Product opens the new Customer's page
  kind: product
  actor: agent-manager
  entities:
  - entity: customer
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::customer
  capability: create-customer
- text: The Agent Manager adds Contacts to the Customer
  kind: actor
  actor: agent-manager
  entities:
  - entity: customer-membership
    effect: creates
    facts:
    - Role
  - entity: contact
    effect: reads
    facts: []
  - entity: customer
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::customer
  capability: add-customer-contacts
---

# Create a customer and add its contacts

## Trigger

An Agent Manager creates a customer.

## Outcome

The Agent Manager is on the new customer's page and has added contacts.
