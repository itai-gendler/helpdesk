---
kind: primary
routes:
  main: Agent portal
steps:
- text: An assigned Ticket is saved and meets its Assignment rule's unassignment condition
  kind: condition
  unattended: true
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Team
    - Assigned agents
  - entity: assignment-rule
    effect: reads
    facts:
    - Unassignment condition
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product removes the rule's assignment from the Ticket
  kind: product
  entities:
  - entity: ticket
    effect: changes
    facts:
    - Assigned agents
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_team/hd_team.py
---

# Unassign a ticket by assignment rule

## Trigger

An assigned Ticket is saved and now meets the unassignment condition of the Assignment rule that assigned it.

## Outcome

The rule's assignment is removed, so another rule may assign the Ticket.

## Edge cases

- A team's rotation unassigns a ticket that moves to another team.
