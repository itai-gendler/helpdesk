---
kind: primary
routes:
  main: Agent portal
steps:
- text: The Agent picks an availability
  kind: actor
  actor: agent
  entities:
  - entity: agent
    effect: reads
    facts:
    - Availability
  contexts:
    main:
      place: helpdesk-web::agent-portal
- text: The Product saves the availability and shares it live
  kind: product
  actor: agent
  entities:
  - entity: agent
    effect: changes
    facts:
    - Availability
    - Availability changed on
  contexts:
    main:
      place: helpdesk-web::agent-portal
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_agent/hd_agent.py
---

# Change one's availability

## Trigger

An Agent steps away or comes back.

## Outcome

Everyone sees the Agent's new availability, and automatic assignment takes it into account.

## Edge cases

- Only an enabled agent status may be chosen.
