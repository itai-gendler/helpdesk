---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager cancels a pending Invitation
  kind: actor
  actor: agent-manager
  entities:
  - entity: invitation
    effect: reads
    facts:
    - Email
    - Role
    - Status
  contexts:
    main:
      place: helpdesk-web::administration::invite-agents
- text: The Product cancels the Invitation
  kind: product
  actor: agent-manager
  entities:
  - entity: invitation
    effect: changes
    facts:
    - Status
  contexts:
    main:
      place: helpdesk-web::administration::invite-agents
---

# Cancel an invitation

## Trigger

An Agent Manager withdraws a pending Invitation.

## Outcome

The Invitation is cancelled and can no longer be accepted.
