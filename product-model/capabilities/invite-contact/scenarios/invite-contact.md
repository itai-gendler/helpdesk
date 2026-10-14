---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent Manager chooses Invite as User
  kind: actor
  actor: agent-manager
  entities:
  - entity: contact
    effect: reads
    facts:
    - Email
  contexts:
    main:
      place: helpdesk-web::agent-portal::contact
- text: The Product emails the Contact an Invitation
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
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::contact
references:
- kind: code
  role: implementation
  target: desk/src/pages/contact/Contact.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/hooks/user_invitation.py
---

# Invite a contact to the portal

## Trigger

An Agent Manager invites a Contact who has no portal account.

## Outcome

The Contact receives an Invitation; accepting it gives them a portal account linked to this Contact.

## Edge cases

- A pending invitation can be sent again; an expired one shows as expired.
