---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent Manager picks the role
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
- text: The Product saves the role and updates the Contact's portal roles
  kind: product
  actor: agent-manager
  entities:
  - entity: customer-membership
    effect: changes
    facts:
    - Role
  - entity: contact
    effect: reads
    facts:
    - Portal account
  contexts:
    main:
      place: helpdesk-web::agent-portal::customer
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_customer/hd_customer.py
---

# Change a contact's role in a customer

## Trigger

An Agent Manager makes a Contact a Customer Manager, or back to a Customer.

## Outcome

The membership has the new role, and the Contact's portal access follows it.

## Edge cases

- A contact who still manages another customer keeps the manager role there.
- The primary contact is always a Customer Manager.
