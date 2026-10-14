---
kind: primary
routes:
  main: Agent portal
steps:
- text: An unassigned Ticket is saved and matches an enabled Assignment rule active today
  kind: condition
  unattended: true
  entities:
  - entity: ticket
    effect: reads
    facts:
    - Status
    - Team
    - Priority
    - Ticket type
  - entity: assignment-rule
    effect: reads
    facts:
    - Assignment condition
    - Assignment days
    - Priority
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product picks an assignee by the rule's routing, preferring Active, then Away Agents
  kind: product
  entities:
  - entity: assignment-rule
    effect: changes
    facts:
    - Last assigned agent
  - entity: agent
    effect: reads
    facts:
    - Availability
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
- text: The Product assigns the picked Agent to the Ticket
  kind: product
  entities:
  - entity: ticket
    effect: changes
    facts:
    - Assigned agents
  - entity: agent
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::ticket
references:
- kind: code
  role: implementation
  target: helpdesk/overrides/assignment_rule.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_team/hd_team.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_settings/hd_settings.py
---

# Assign a ticket by assignment rule

## Trigger

A Ticket with no assignee is saved while an enabled Assignment rule, active today, matches it.

## Outcome

The Ticket is assigned to one of the rule's assignees.

## Decision points

### Which rule

Do several enabled rules match?

- Several match → the highest-priority rule assigns
- One matches → that rule assigns

## Edge cases

- Unavailable agents are picked only when no assignee is Active or Away.
