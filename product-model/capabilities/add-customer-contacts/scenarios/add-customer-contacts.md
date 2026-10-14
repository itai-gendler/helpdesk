---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent Manager enters people or email addresses and a role
  kind: actor
  actor: agent-manager
  entities:
  - entity: customer
    effect: reads
    facts:
    - Customer name
  contexts:
    main:
      place: helpdesk-web::agent-portal::customer
- text: The Product adds each Contact with a portal account as a member with that role
  kind: product
  actor: agent-manager
  entities:
  - entity: customer-membership
    effect: creates
    facts:
    - Role
  - entity: contact
    effect: reads
    facts:
    - Email
    - Portal account
  contexts:
    main:
      place: helpdesk-web::agent-portal::customer
- text: The Product emails an Invitation to everyone else
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
  contexts:
    main:
      place: helpdesk-web::agent-portal::customer
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_customer/hd_customer.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/hooks/user_invitation.py
---

# Add contacts to a customer

## Trigger

An Agent Manager adds people to a Customer with a role.

## Outcome

People with a portal account belong to the Customer; the rest are invited and join when they accept.

## Edge cases

- A contact already in the customer is not added twice.
- A contact with no email address is refused.
