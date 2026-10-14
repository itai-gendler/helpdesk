---
kind: primary
routes:
  main: Administration
steps:
- text: The Agent Manager chooses Disable Agent
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
- text: The Product makes the Agent inactive
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
- kind: code
  role: implementation
  target: helpdesk/utils.py
---

# Disable an agent

## Trigger

An Agent Manager disables an Agent.

## Outcome

The Agent keeps their roles but no longer has agent access.
