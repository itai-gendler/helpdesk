---
kind: person
acts: external
relations:
- entity: ticket
  verb: is assigned to
  cardinality: many-to-many
- entity: notification
  verb: receives
  cardinality: one-to-many
- entity: saved-reply
  verb: writes
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_agent/hd_agent.py
- kind: code
  role: implementation
  target: helpdesk/utils.py
---

# Agent

A member of the support staff who works tickets in the agent portal. Every agent has an agent record that can be deactivated; a deactivated agent keeps their roles but loses agent access.

## Information kept

- **Agent name** — the agent's display name, kept in step with their user
- **Active** — whether the agent may work in the agent portal
- **Image** — the agent's picture
- **Availability** — a configured agent status in the Active, Away or Unavailable category
- **Availability changed on** — when and by whom availability last changed
- **Role** — Agent or Manager
