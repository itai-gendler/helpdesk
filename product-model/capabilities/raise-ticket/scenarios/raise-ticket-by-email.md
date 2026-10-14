---
kind: primary
routes:
  main: Support email
steps:
- text: The Contact emails the support address
  kind: actor
  actor: contact
  entities: []
  contexts:
    main:
      place: support-email
- text: The Product creates the Ticket from the email, matching the Contact by address
  kind: product
  actor: contact
  entities:
  - entity: ticket
    effect: creates
    to: Open
    facts:
    - Subject
    - Description
    - Status
    - Priority
    - Ticket type
    - Raised by
    - Customer
    - Raised via portal
    - Raised outside working hours
    - Template fields
    - SLA policy
    - SLA clock start
    - First response due
    - Resolution due
    - SLA status
  - entity: reply
    effect: creates
    facts:
    - Message
    - Sender
    - Direction
    - Attachments
    - Sent at
    with: ticket
  contexts:
    main:
      place: support-email
- text: The Product emails the Contact that the Ticket was received
  kind: product
  actor: contact
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Subject
  - entity: helpdesk-settings
    effect: reads
    facts:
    - Acknowledgement email
  contexts:
    main:
      place: support-email
references:
- kind: code
  role: implementation
  target: helpdesk/overrides/email_account.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Raise a ticket by email

## Trigger

A Contact emails the support address with a new message, not a reply in an existing ticket's thread.

## Outcome

A new Ticket holds the email as its opening Reply and the Contact may receive an acknowledgement.

## Decision points

### Customer

Did the requester choose a customer?

- A customer was chosen → the ticket keeps it
- None was chosen, auto-set is on and the contact belongs to exactly one customer → the ticket takes that customer
- Otherwise → the ticket has no customer

### Automatic assignment

Does an enabled assignment rule active today match the new ticket?

- A rule matches → the ticket is assigned by that rule's routing, highest-priority rule first
- No rule matches → the ticket stays unassigned

### Acknowledgement

Is the acknowledgement email enabled?

- Enabled → the requester receives the acknowledgement
- Disabled → no acknowledgement is sent

## Edge cases

- Bounces, delivery reports and other machine-generated mail are set aside instead of raising a ticket; a bounce of an agent's reply leaves a note on that ticket.
- Out-of-office replies are not set aside.
