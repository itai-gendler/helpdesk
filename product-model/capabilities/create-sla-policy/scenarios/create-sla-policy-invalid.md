---
kind: validation
routes:
  main: Administration
steps:
- text: The Agent Manager saves the policy
  kind: actor
  actor: agent-manager
  entities: []
  contexts:
    main:
      place: helpdesk-web::administration::sla-policy
- text: The Product refuses the SLA policy
  kind: condition
  entities:
  - entity: sla-policy
    effect: reads
    facts:
    - Priority targets
    - Working hours
    - Apply to resolution
    - Condition
  contexts:
    main:
      place: helpdesk-web::administration::sla-policy
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.py
---

# Refuse an inconsistent SLA policy

## Trigger

An Agent Manager saves an SLA policy whose targets or working hours do not hold together.

## Outcome

Nothing is saved and the Agent Manager is told which row is wrong.

## Edge cases

- A priority without a first response time is refused.
- A first response time longer than the resolution time is refused while resolution targets apply.
- A repeated priority, more than one default priority, or none, is refused.
- A repeated workday, or a start time not before the end time, is refused.
