---
kind: primary
routes:
  main: Agent portal
steps:
- text: The hourly run takes each open Ticket with an SLA policy
  kind: condition
  unattended: true
  entities:
  - entity: ticket
    effect: reads
    facts:
    - SLA policy
    - First response due
    - Resolution due
    - First responded on
    - Resolution date
    - On hold since
  - entity: sla-policy
    effect: reads
    facts: []
  contexts:
    main:
      place: helpdesk-web::agent-portal::tickets
- text: The Product sets the Ticket's SLA status
  kind: product
  entities:
  - entity: ticket
    effect: changes
    facts:
    - SLA status
  contexts:
    main:
      place: helpdesk-web::agent-portal::tickets
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.py
---

# Mark tickets that missed an SLA target

## Trigger

The hourly run finds open Tickets with an SLA policy.

## Outcome

Each such Ticket's SLA status says whether a target has been missed.

## Decision points

### SLA status

Which target state holds?

- A due time has passed unmet → Failed
- On hold → Paused
- Not yet answered → First Response Due
- Answered, resolution target applies, not resolved → Resolution Due
- Otherwise → Fulfilled

## Edge cases

- A paused ticket is measured against when it went on hold.
