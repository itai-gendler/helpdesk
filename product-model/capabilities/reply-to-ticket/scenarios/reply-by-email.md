---
kind: primary
routes:
  main: Support email
steps:
- text: The Contact replies to an email in the thread
  kind: actor
  actor: contact
  entities: []
  contexts:
    main:
      place: support-email
- text: The Product adds the Reply to the Ticket and moves it to its reopen status
  kind: product
  actor: contact
  entities:
  - entity: reply
    effect: creates
    facts:
    - Message
    - Sender
    - Direction
    - Attachments
    - Sent at
  - entity: ticket
    effect: changes
    from: Paused
    to: Open
    facts:
    - Status
    - Last customer response
  contexts:
    main:
      place: support-email
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/overrides/email_account.py
---

# Reply in the ticket's email thread

## Trigger

A Contact answers an agent's email about a paused Ticket.

## Outcome

The email joins the Ticket's conversation and the Ticket is back in front of the support team.

## Decision points

### Reopen or start over

Has an agent already replied on the ticket?

- An agent has replied → the ticket moves to its reopen status
- No agent reply yet → the ticket moves to its default status

## Edge cases

- A reply to a merged ticket joins the ticket it was merged into.
