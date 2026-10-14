---
kind: edge
routes:
  main: Agent portal
steps:
- text: The Agent sends a message
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Subject
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product finds no outgoing email account for the Ticket and refuses
  kind: condition
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts: []
  - entity: email-account
    effect: reads
    facts:
    - Outgoing
    - Default outgoing
  - entity: helpdesk-settings
    effect: reads
    facts:
    - Skip email workflow
    - Reply from agent email
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Refuse an agent reply with no outgoing email account

## Trigger

An Agent replies while email is on but no outgoing email account is available for the Ticket.

## Outcome

Nothing is written; the Agent is told to set up a default outgoing email account.
