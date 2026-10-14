---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager enters the policy's details, conditions, targets, working hours, holiday list and statuses
  kind: actor
  actor: agent-manager
  entities:
  - entity: holiday-list
    effect: reads
    facts:
    - Name
  contexts:
    main:
      place: helpdesk-web::administration::sla-policy
- text: The Product creates the SLA policy
  kind: product
  actor: agent-manager
  entities:
  - entity: sla-policy
    effect: creates
    to: Enabled
    facts:
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
  contexts:
    main:
      place: helpdesk-web::administration::sla-policy
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.py
- kind: code
  role: implementation
  target: desk/src/components/Settings/Sla/SlaPolicyView.vue
---

# Create an SLA policy

## Trigger

An Agent Manager sets up a new SLA policy.

## Outcome

The SLA policy exists and applies to matching tickets from their next change.

## Decision points

### Default policy

Is the new policy marked default?

- Yes → the previous default policy stops being the default and the manager is told it now needs a condition
- No → the previous default stays
