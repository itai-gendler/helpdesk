---
kind: primary
routes:
  main: Customer portal
steps:
- text: The Contact chooses Close
  kind: actor
  actor: contact
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Status
  contexts:
    main:
      place: helpdesk-web::customer-portal::ticket
- text: The Contact picks a rating and a feedback option and optionally writes feedback
  kind: actor
  actor: contact
  entities: []
  contexts:
    main:
      place: helpdesk-web::customer-portal::ticket
- text: The Product closes and rates the Ticket
  kind: product
  actor: contact
  entities:
  - entity: ticket
    effect: changes
    from: Paused
    to: Closed
    facts:
    - Status
    - Feedback
    - Rating
    - Feedback comment
    - Resolution date
    - Resolution time
    - SLA status
  contexts:
    main:
      place: helpdesk-web::customer-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: desk/src/pages/ticket/TicketFeedback.vue
---

# Close a ticket with a rating

## Trigger

A Contact closes a Ticket an agent has replied on while feedback is mandatory.

## Outcome

The Ticket is Closed with the Contact's rating and feedback.

## Edge cases

- A rated ticket can no longer be changed by its requester.
