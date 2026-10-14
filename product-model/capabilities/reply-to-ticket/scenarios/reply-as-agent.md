---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent writes the message and chooses its recipients
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Subject
    - Raised by
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product adds the Reply and records the response on the Ticket
  kind: product
  actor: agent
  entities:
  - entity: reply
    effect: creates
    facts:
    - Message
    - Sender
    - Direction
    - To
    - CC
    - BCC
    - Attachments
    - Sent at
  - entity: ticket
    effect: changes
    facts:
    - First responded on
    - First response time
    - Last agent response
    - SLA status
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product emails the Reply from the Ticket's email account
  kind: product
  actor: agent
  entities:
  - entity: reply
    effect: reads
    facts:
    - Message
    - To
    - CC
    - BCC
    - Attachments
  - entity: ticket
    effect: reads
    facts: []
  - entity: email-account
    effect: reads
    facts:
    - Outgoing
  - entity: helpdesk-settings
    effect: reads
    facts:
    - Reply from agent email
    - Skip email workflow
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Reply to the requester as an agent

## Trigger

An Agent answers an open Ticket from the agent portal.

## Outcome

The Reply is in the conversation, emailed to its recipients, and the Ticket's first response is recorded.

## Decision points

### Email

Is email on for agent replies?

- Skip email workflow is off and reply from agent email is enabled → the reply is emailed, threaded under the conversation's last emailed message
- Otherwise → the reply is kept on the ticket only

### Status after replying

Is Auto update status set?

- Set → the ticket moves to that status
- Not set → the ticket keeps its status

## Edge cases

- Tickets raised in the Helpdesk get the reply inside the reply from agent email content, with a link to the ticket in the portal; email-raised tickets get the bare reply.
- Only the first agent reply sets the first response.
