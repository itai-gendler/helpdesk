---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent changes the Ticket's details
  kind: actor
  actor: agent
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Subject
    - Priority
    - Ticket type
    - Team
    - Customer
    - Template fields
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product saves the details and reapplies the SLA policy selection
  kind: product
  actor: agent
  entities:
  - entity: ticket
    effect: changes
    facts:
    - Subject
    - Priority
    - Ticket type
    - Team
    - Customer
    - Template fields
    - SLA policy
    - First response due
    - Resolution due
    - SLA status
  - entity: sla-policy
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product drops an assignee outside a new Team and lets that Team's rotation assign
  kind: product
  actor: agent
  entities:
  - entity: ticket
    effect: changes
    facts:
    - Assigned agents
  - entity: team
    effect: reads
    facts:
    - Members
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/utils.py
---

# Change a ticket's details as an agent

## Trigger

An Agent changes a Ticket's priority, type, team, customer or subject.

## Outcome

The Ticket shows the new details and is retimed by whichever SLA policy now applies.

## Decision points

### New team

Did the team change on an open ticket whose assignee is not in the new team, while that team's rotation has assignees?

- Yes → the assignment is cleared and the new team's rotation may assign
- No → the assignees stay

## Edge cases

- A ticket that no policy matches any more loses its SLA timing; a failed SLA status stays failed.
- The clock start stays, so moving a ticket in and out of a policy gains it no time.
