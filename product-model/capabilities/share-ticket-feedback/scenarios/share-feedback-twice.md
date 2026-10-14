---
kind: validation
routes:
  main: Ticket feedback
steps:
- text: The Contact submits the feedback form again
  kind: actor
  actor: contact
  entities: []
  contexts:
    main:
      place: helpdesk-web::ticket-feedback::rate-support-experience
- text: The Product refuses because the Ticket was already rated through its link
  kind: condition
  actor: contact
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Rating
  contexts:
    main:
      place: helpdesk-web::ticket-feedback::rate-support-experience
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_email_feedback/hd_email_feedback.py
---

# Refuse a second rating from the feedback email

## Trigger

A Contact submits the feedback form again for a Ticket already rated through its link.

## Outcome

Nothing changes; the Contact is told feedback was already given.

## Edge cases

- A link whose ticket no longer exists is refused.
