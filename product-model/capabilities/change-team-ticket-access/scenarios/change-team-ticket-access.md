---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager picks the Team's access
  kind: actor
  actor: agent-manager
  entities:
  - entity: team
    effect: reads
    facts:
    - Ticket access
  contexts:
    main:
      place: helpdesk-web::administration::team
- text: The Product saves the Team's access
  kind: product
  actor: agent-manager
  entities:
  - entity: team
    effect: changes
    facts:
    - Ticket access
  contexts:
    main:
      place: helpdesk-web::administration::team
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Teams/TeamEdit.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Change a team's ticket access

## Trigger

An Agent Manager lets a Team access all team tickets, or only its own.

## Outcome

The Team's members see tickets accordingly while tickets are restricted by team.
