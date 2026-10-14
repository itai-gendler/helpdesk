---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager chooses Delete and confirms
  kind: actor
  actor: agent-manager
  entities:
  - entity: holiday-list
    effect: reads
    facts:
    - Name
  contexts:
    main:
      place: helpdesk-web::administration::holiday-lists
- text: The Product deletes the Holiday list
  kind: product
  actor: agent-manager
  entities:
  - entity: holiday-list
    effect: removes
  contexts:
    main:
      place: helpdesk-web::administration::holiday-lists
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Holiday/HolidayListItem.vue
---

# Delete a holiday list

## Trigger

An Agent Manager deletes a Holiday list.

## Outcome

The Holiday list is gone.
