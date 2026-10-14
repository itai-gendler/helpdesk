---
kind: primary
routes:
  main: Ticket feedback
steps:
- text: The Contact picks a rating and optionally writes feedback
  kind: actor
  actor: contact
  entities: []
  contexts:
    main:
      place: helpdesk-web::ticket-feedback::rate-support-experience
- text: The Product rates the Ticket the link belongs to and closes it
  kind: product
  actor: contact
  entities:
  - entity: ticket
    effect: changes
    facts:
    - Rating
    - Feedback comment
    - Status
  contexts:
    main:
      place: helpdesk-web::ticket-feedback::rate-support-experience
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_email_feedback/hd_email_feedback.py
---

# Rate support from the feedback email

## Trigger

A Contact follows the feedback link emailed when their Ticket reached the configured status.

## Outcome

The Ticket is Closed and carries the Contact's rating and comment.
