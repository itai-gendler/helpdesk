---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent Manager enters the name, email, phone and picture, and chooses whether to invite
  kind: actor
  actor: agent-manager
  entities: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::contacts
- text: The Product creates the Contact
  kind: product
  actor: agent-manager
  entities:
  - entity: contact
    effect: creates
    facts:
    - Name
    - Email
    - Phone
    - Image
  contexts:
    main:
      place: helpdesk-web::agent-portal::contacts
- text: The Product emails the Contact an Invitation to the portal
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
  contexts:
    main:
      place: helpdesk-web::agent-portal::contacts
references:
- kind: code
  role: implementation
  target: helpdesk/api/contact.py
---

# Create a contact

## Trigger

An Agent Manager adds a person who asks for support.

## Outcome

The Contact exists, and is invited to the portal if chosen.

## Decision points

### Invite

Did the manager choose to invite?

- Yes → the contact is invited as a Customer
- No → no invitation is sent

## Edge cases

- A phone number without a country code is refused.
