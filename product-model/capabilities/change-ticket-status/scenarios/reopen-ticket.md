---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent picks an open status
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Status
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product reopens the Ticket, credits the pause as hold time and moves its resolution target
  kind: product
  actor: agent
  entities:
  - entity: ticket
    effect: changes
    from: Paused
    to: Open
    facts:
    - Status
    - On hold since
    - Total hold time
    - Resolution due
    - SLA status
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product notifies the Ticket's assigned Agent that it was reopened
  kind: product
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Assigned agents
  - entity: agent
    effect: reads
    facts: []
  - entity: notification
    effect: creates
    facts:
    - Kind
    - Subject
    - From
    - Read
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.py
- kind: code
  role: implementation
  target: helpdesk/notifications.py
---

# Reopen a paused ticket

## Trigger

An Agent moves a paused Ticket back to an Open-category status.

## Outcome

The Ticket is open again; its pause is added to its hold time and its resolution target moves later.

## Edge cases

- Reopening a resolved ticket counts the time it spent resolved as hold time and clears its resolution.
