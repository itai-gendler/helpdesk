---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager switches the policy off
  kind: actor
  actor: agent-manager
  entities:
  - entity: sla-policy
    effect: reads
    facts:
    - Name
  contexts:
    main:
      place: helpdesk-web::administration::sla-policies
- text: The Product disables the SLA policy
  kind: product
  actor: agent-manager
  entities:
  - entity: sla-policy
    effect: changes
    from: Enabled
    to: Disabled
    facts: []
  contexts:
    main:
      place: helpdesk-web::administration::sla-policies
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Sla/SlaPolicyListItem.vue
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.py
---

# Disable an SLA policy

## Trigger

An Agent Manager switches an SLA policy off.

## Outcome

The policy applies to no ticket; its open tickets lose it at their next update unless another policy matches.

## Edge cases

- The manager is warned how many open tickets are on the policy.
