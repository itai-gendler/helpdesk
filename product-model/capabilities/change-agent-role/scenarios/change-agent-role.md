---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager picks Manager or Agent for the Agent
  kind: actor
  actor: agent-manager
  entities:
  - entity: agent
    effect: reads
    facts:
    - Agent name
  contexts:
    main:
      place: helpdesk-web::administration::agents
- text: The Product updates the Agent's role
  kind: product
  actor: agent-manager
  entities:
  - entity: agent
    effect: changes
    facts:
    - Role
  contexts:
    main:
      place: helpdesk-web::administration::agents
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Agents.vue
---

# Change an agent's role

## Trigger

An Agent Manager makes an Agent a Manager, or back.

## Outcome

The person's Helpdesk role is the chosen one.
