---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager chooses Delete and confirms
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
- text: The Product deletes the SLA policy
  kind: product
  actor: agent-manager
  entities:
  - entity: sla-policy
    effect: removes
    from: Enabled
  contexts:
    main:
      place: helpdesk-web::administration::sla-policies
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Sla/SlaPolicyListItem.vue
---

# Delete an SLA policy

## Trigger

An Agent Manager deletes an SLA policy.

## Outcome

The SLA policy is gone.
