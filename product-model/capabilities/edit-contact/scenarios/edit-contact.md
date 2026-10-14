---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent Manager changes the details and saves
  kind: actor
  actor: agent-manager
  entities:
  - entity: contact
    effect: reads
    facts:
    - Name
    - Email
    - Phone
    - Image
  contexts:
    main:
      place: helpdesk-web::agent-portal::contact
- text: The Product saves the Contact
  kind: product
  actor: agent-manager
  entities:
  - entity: contact
    effect: changes
    facts:
    - Name
    - Email
    - Phone
    - Image
  contexts:
    main:
      place: helpdesk-web::agent-portal::contact
references:
- kind: code
  role: implementation
  target: helpdesk/api/contact.py
---

# Edit a contact

## Trigger

An Agent Manager updates a Contact's details.

## Outcome

The Contact has the new details; a portal user's picture and time zone follow.
