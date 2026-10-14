---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager changes the policy and saves
  kind: actor
  actor: agent-manager
  entities:
  - entity: sla-policy
    effect: reads
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
- text: The Product saves the SLA policy
  kind: product
  actor: agent-manager
  entities:
  - entity: sla-policy
    effect: changes
    facts:
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
---

# Edit an SLA policy

## Trigger

An Agent Manager changes an SLA policy.

## Outcome

The SLA policy has the new settings; open tickets are retimed the next time they change.

## Edge cases

- Removing a priority that open tickets on the policy use, or unticking Default, warns how many open tickets will lose the policy at their next update.
