---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent Manager enters the organization's name, type, domain, country and logo, and optionally a primary person's details
  kind: actor
  actor: agent-manager
  entities: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::customers
- text: The Product creates the Customer with the primary Contact as its Customer Manager membership
  kind: product
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
  - entity: customer-membership
    effect: creates
    facts:
    - Role
    with: customer
  - entity: contact
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::customers
- text: The Product emails the primary Contact an Invitation when they have no portal account
  kind: product
  actor: agent-manager
  entities:
  - entity: invitation
    effect: creates
    facts:
    - Email
    - Role
    - Invited by
    - Status
  - entity: contact
    effect: reads
    facts:
    - Email
    - Portal account
  contexts:
    main:
      place: helpdesk-web::agent-portal::customers
- text: The new Customer's page opens
  kind: condition
  entities:
  - entity: customer
    effect: reads
    facts: []
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

# Create a customer

## Trigger

An Agent Manager adds a new customer organization from the customer list.

## Outcome

The Customer exists and opens on its own page; a named primary contact belongs to it as its Customer Manager.

## Decision points

### Primary contact

Does the primary contact's email belong to an existing Contact with a portal account?

- Yes → they are added directly
- Existing contact without an account, or a new email → the contact is created if needed and invited by email
