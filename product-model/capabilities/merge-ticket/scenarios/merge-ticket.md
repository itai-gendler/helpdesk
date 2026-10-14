---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent chooses the Ticket to merge into
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    as: target
    effect: reads
    facts:
    - Subject
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product copies the source's Replies, Comments and files to the target Ticket
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
  - entity: comment
    effect: creates
    facts:
    - Content
    - Author
    - Mentions
    - Attachments
    - Pinned
  - entity: ticket
    as: target
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product closes the source Ticket as merged and replies on it with a link to the target
  kind: product
  actor: agent
  entities:
  - entity: ticket
    as: source
    effect: changes
    from: Open
    to: Closed
    facts:
    - Status
    - Merged with
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/api.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Merge a ticket into another

## Trigger

An Agent finds that an open Ticket duplicates another and merges it into that one.

## Outcome

The target Ticket holds both conversations; the source is Closed, points to the target, and its requester is told where it went.

## Edge cases

- Copied comments arrive unpinned on the target.
- Later replies to the source go to the target, following a chain of merges to the last unmerged ticket.
