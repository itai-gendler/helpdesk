---
kind: primary
routes:
  main: Customer portal
steps:
- text: The Contact writes a message with any attachments
  kind: actor
  actor: contact
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Subject
    - Status
  contexts:
    main:
      place: helpdesk-web::customer-portal::ticket
- text: The Product adds the Reply and moves the Ticket to its reopen status
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
      place: helpdesk-web::customer-portal::ticket
- text: The Product emails the Reply to the Ticket's assigned Agent
  kind: product
  actor: contact
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Assigned agents
  - entity: reply
    effect: reads
    facts:
    - Message
  - entity: helpdesk-settings
    effect: reads
    facts:
    - Reply from contact email
  - entity: agent
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::customer-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Reply in the customer portal

## Trigger

A Contact answers an agent on a paused Ticket in the customer portal.

## Outcome

The Reply is in the conversation and the Ticket is back in its reopen status.

## Decision points

### Notify assigned agents

Is the reply from contact email enabled and is anyone assigned?

- Enabled and assigned → each assigned agent is emailed the reply
- Otherwise → no agent is emailed

## Edge cases

- The reopen status is the ticket's SLA policy's, or the Helpdesk's when the policy names none.
- Assigned agents are notified in the Helpdesk that the ticket was reopened.
