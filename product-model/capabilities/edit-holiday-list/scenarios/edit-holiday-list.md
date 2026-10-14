---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager changes the list and saves
  kind: actor
  actor: agent-manager
  entities:
  - entity: holiday-list
    effect: reads
    facts:
    - Name
    - Description
    - Valid from
    - Valid to
    - Holidays
    - Recurring holidays
  contexts:
    main:
      place: helpdesk-web::administration::holiday-list
- text: The Product saves the Holiday list
  kind: product
  actor: agent-manager
  entities:
  - entity: holiday-list
    effect: changes
    facts:
    - Name
    - Description
    - Valid from
    - Valid to
    - Holidays
    - Recurring holidays
  contexts:
    main:
      place: helpdesk-web::administration::holiday-list
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Holiday/HolidayView.vue
---

# Edit a holiday list

## Trigger

An Agent Manager changes a Holiday list.

## Outcome

SLA policies using the list count working time with the changed holidays.
