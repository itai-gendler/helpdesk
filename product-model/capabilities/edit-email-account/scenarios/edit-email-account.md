---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager changes the account and saves
  kind: actor
  actor: agent-manager
  entities:
  - entity: email-account
    effect: reads
    facts:
    - Account name
    - Email address
    - Service
    - Incoming
    - Outgoing
    - Default incoming
    - Default outgoing
  contexts:
    main:
      place: helpdesk-web::administration::email-account
- text: The Product saves the Email account
  kind: product
  actor: agent-manager
  entities:
  - entity: email-account
    effect: changes
    facts:
    - Account name
    - Email address
    - Service
    - Incoming
    - Outgoing
    - Default incoming
    - Default outgoing
    - Credentials
  contexts:
    main:
      place: helpdesk-web::administration::email-account
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/EmailEdit.vue
---

# Edit a mailbox

## Trigger

An Agent Manager changes an Email account.

## Outcome

The Email account uses the new settings.
