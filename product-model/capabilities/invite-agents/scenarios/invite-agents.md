---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager enters email addresses and a role
  kind: actor
  actor: agent-manager
  entities: []
  contexts:
    main:
      place: helpdesk-web::administration::invite-agents
- text: The Product emails each person an Invitation
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
      place: helpdesk-web::administration::invite-agents
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/hooks/user_invitation.py
- kind: code
  role: implementation
  target: helpdesk/overrides/user_invitation.py
---

# Invite agents

## Trigger

An Agent Manager invites colleagues by email with a role.

## Outcome

Each person receives an Invitation; accepting it makes them an agent with that role.

## Edge cases

- The invitation email carries the brand name when one is set.
