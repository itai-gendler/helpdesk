---
kind: primary
routes:
  main: Customer portal
steps:
- text: The daily run finds a Ticket in the auto-close status whose last Reply is older than the configured days
  kind: condition
  unattended: true
  entities:
  - entity: helpdesk-settings
    effect: reads
    facts:
    - Auto-close
    - Auto-close status
    - Auto-close after days
  - entity: reply
    effect: reads
    facts:
    - Sent at
  - entity: ticket
    effect: reads
    facts:
    - Status
  contexts:
    main:
      place: helpdesk-web::customer-portal::ticket
- text: The Product closes the Ticket
  kind: product
  entities:
  - entity: ticket
    effect: changes
    from: Paused
    to: Closed
    facts:
    - Status
  contexts:
    main:
      place: helpdesk-web::customer-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Close a stale ticket automatically

## Trigger

Once a day, with auto-close on, a Ticket in the auto-close status has had no message for the configured number of days.

## Outcome

The Ticket is Closed and its activity says it closed automatically after the days of inactivity.

## Edge cases

- A ticket with no reply at all is never closed automatically.
- Internal comments do not count as activity.
- A ticket that fails to close is logged and skipped.
