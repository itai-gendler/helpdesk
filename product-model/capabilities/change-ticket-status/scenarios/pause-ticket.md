---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent picks a paused status
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
- text: The Product pauses the Ticket and holds its SLA clock
  kind: product
  actor: agent
  entities:
  - entity: ticket
    effect: changes
    from: Open
    to: Paused
    facts:
    - Status
    - On hold since
    - First response due
    - Resolution due
    - Resolution date
    - Resolution time
    - SLA status
    - First responded on
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
---

# Put a ticket on hold

## Trigger

An Agent moves an open Ticket to a Paused-category status, such as Replied.

## Outcome

The Ticket is paused and its SLA clock is on hold.

## Edge cases

- A ticket with no first response yet counts this move as its first response.
- Moving several selected tickets from the list changes each the same way.
