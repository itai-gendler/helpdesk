---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent picks Closed
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Status
    - Resolution date
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product closes the Ticket without restamping its resolution
  kind: product
  actor: agent
  entities:
  - entity: ticket
    effect: changes
    from: Resolved
    to: Closed
    facts:
    - Status
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

# Close a resolved ticket

## Trigger

An Agent moves a resolved Ticket to Closed.

## Outcome

The Ticket is Closed and keeps the resolution it already had.

## Decision points

### Feedback email

Is the share feedback email enabled for Closed (its default status), and was the ticket raised by email and not yet rated?

- Yes → the requester is emailed a link to rate the support
- No → no feedback email is sent
