---
entities:
- entity: holiday-list
  shows: &id001
  - Name
  - Description
  - Valid from
  - Valid to
  - Holidays
  - Recurring holidays
  collects: *id001
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Holiday/HolidayView.vue
---

# Holiday list

Creating or editing one holiday list, by calendar or list.
