---
entities:
- entity: sla-policy
  shows: &id001
  - Name
  - Description
  - Default
  - Rank
  - Condition
  - Valid from
  - Valid to
  - Priority targets
  - Apply to resolution
  - Working hours
  - Holiday list
  - Default ticket status
  - Reopen status
  collects: *id001
- entity: holiday-list
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Sla/SlaPolicyView.vue
---

# SLA policy

Creating or editing one SLA policy.
