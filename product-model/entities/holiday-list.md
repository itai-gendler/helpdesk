---
domain: business-holidays
relations:
- entity: sla-policy
  verb: is used by
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_holiday_list/hd_service_holiday_list.json
- kind: code
  role: implementation
  target: desk/src/components/Settings/Holiday/HolidayView.vue
---

# Holiday list

A named set of holidays, one-off dates and recurring days such as weekends, over a date range. An SLA policy's holiday list takes those days out of its working time.

## Information kept

- **Name** — the list's name
- **Description** — what the list is for
- **Valid from** — the first day the list covers
- **Valid to** — the last day the list covers
- **Holidays** — each holiday's date and description
- **Recurring holidays** — weekdays that are holidays every week within the range
