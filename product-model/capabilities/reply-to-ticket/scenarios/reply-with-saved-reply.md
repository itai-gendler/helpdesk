---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent picks a Saved reply, which fills the editor with its message rendered for the Ticket
  kind: actor
  actor: agent
  entities:
  - entity: saved-reply
    effect: reads
    facts:
    - Title
    - Message
    - Actions
  - entity: ticket
    effect: reads
    facts:
    - Subject
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product adds and sends the Reply
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
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product applies the Saved reply's actions to the Ticket
  kind: product
  actor: agent
  entities:
  - entity: saved-reply
    effect: reads
    facts:
    - Actions
  - entity: ticket
    effect: changes
    facts:
    - Priority
    - Ticket type
    - Team
    - Assigned agents
    - Tags
  - entity: comment
    effect: creates
    facts:
    - Content
    - Author
    - Mentions
    - Attachments
    - Pinned
    - Reactions
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/api/saved_replies.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_saved_reply/hd_saved_reply.py
---

# Reply with a saved reply

## Trigger

An Agent answers a Ticket with a Saved reply that carries actions.

## Outcome

The rendered Reply is sent, then the Saved reply's actions change the Ticket.

## Edge cases

- Actions no longer valid are skipped and reported instead of failing, since the reply is already sent.
- Saved replies are listed only within their scope: one's own personal ones, those of one's teams while tickets are restricted by team, and global ones unless disabled.
