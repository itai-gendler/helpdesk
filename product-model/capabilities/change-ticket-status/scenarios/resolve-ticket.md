---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent picks a resolved status
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
- text: The Product resolves the Ticket and stamps its resolution
  kind: product
  actor: agent
  entities:
  - entity: ticket
    effect: changes
    from: Open
    to: Resolved
    facts:
    - Status
    - Resolution date
    - Resolution time
    - SLA status
    - First responded on
    - First response time
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product emails the requester a feedback link
  kind: product
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Raised by
    - Raised via portal
    - Rating
  - entity: helpdesk-settings
    effect: reads
    facts:
    - Share feedback email
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

# Resolve a ticket

## Trigger

An Agent moves an open Ticket to a Resolved-category status other than Closed.

## Outcome

The Ticket is resolved with its resolution date and resolution time.

## Decision points

### Feedback email

Is the share feedback email enabled for this status, and was the ticket raised by email and not yet rated?

- Yes → the requester is emailed a link to rate the support
- No → no feedback email is sent

## Edge cases

- A ticket with no first response yet counts this move as its first response.
- A late resolution records by how much working time it missed its target.
