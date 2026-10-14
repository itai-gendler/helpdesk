---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager chooses Enable Agent
  kind: actor
  actor: agent-manager
  entities:
  - entity: agent
    effect: reads
    facts:
    - Agent name
    - Active
  contexts:
    main:
      place: helpdesk-web::administration::agents
- text: The Product makes the Agent active
  kind: product
  actor: agent-manager
  entities:
  - entity: agent
    effect: changes
    facts:
    - Active
  contexts:
    main:
      place: helpdesk-web::administration::agents
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/Agents.vue
---

# Enable an agent

## Trigger

An Agent Manager re-enables a disabled Agent.

## Outcome

The Agent can work in the agent portal again.
