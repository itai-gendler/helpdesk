---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent opens their Notifications and chooses Mark all as read
  kind: actor
  actor: agent
  entities:
  - entity: notification
    effect: reads
    facts:
    - Kind
    - Subject
    - From
    - Read
  contexts:
    main:
      place: helpdesk-web::agent-portal::notifications
- text: The Product marks the Agent's Notifications read
  kind: product
  actor: agent
  entities:
  - entity: notification
    effect: changes
    facts:
    - Read
  contexts:
    main:
      place: helpdesk-web::agent-portal::notifications
references:
- kind: code
  role: implementation
  target: helpdesk/notifications.py
---

# Read notifications

## Trigger

An Agent opens their Notifications.

## Outcome

The Agent's Notifications are read.

## Edge cases

- Opening a ticket marks that ticket's notifications read.
