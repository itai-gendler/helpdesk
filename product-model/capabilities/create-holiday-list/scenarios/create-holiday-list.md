---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager enters the name, range, holidays and recurring holidays
  kind: actor
  actor: agent-manager
  entities: []
  contexts:
    main:
      place: helpdesk-web::administration::holiday-list
- text: The Product creates the Holiday list
  kind: product
  actor: agent-manager
  entities:
  - entity: holiday-list
    effect: creates
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

# Create a holiday list

## Trigger

An Agent Manager sets up the business holidays for a period.

## Outcome

The Holiday list exists and can be chosen for SLA policies.
