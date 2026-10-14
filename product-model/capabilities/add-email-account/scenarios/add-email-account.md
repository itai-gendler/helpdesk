---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager picks the service and enters the address, credentials and incoming and outgoing choices
  kind: actor
  actor: agent-manager
  entities: []
  contexts:
    main:
      place: helpdesk-web::administration::email-account
- text: The Product checks the credentials and saves the Email account
  kind: product
  actor: agent-manager
  entities:
  - entity: email-account
    effect: creates
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
  target: helpdesk/api/settings/email.py
---

# Connect a mailbox

## Trigger

An Agent Manager connects the support mailbox.

## Outcome

The Email account pulls new mail into tickets and sends replies, as enabled.

## Edge cases

- Credentials the incoming server rejects are refused and nothing is saved.
- An unsupported service is refused.
