---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager switches the policy on
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
- text: The Product enables the SLA policy
  kind: product
  actor: agent-manager
  entities:
  - entity: sla-policy
    effect: changes
    from: Disabled
    to: Enabled
    facts: []
  contexts:
    main:
      place: helpdesk-web::administration::sla-policies
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Sla/SlaPolicyListItem.vue
---

# Enable an SLA policy

## Trigger

An Agent Manager switches a disabled SLA policy on.

## Outcome

The policy can apply to tickets again.
