---
domain: teams
relations:
- entity: ticket
  verb: handles
  cardinality: one-to-many
- entity: assignment-rule
  verb: rotates through
  cardinality: one-to-one
- entity: agent
  verb: includes
  cardinality: many-to-many
- entity: saved-reply
  verb: shares
  cardinality: many-to-many
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_team/hd_team.py
---

# Team

A group of agents tickets are routed to. Each team keeps its own support rotation, an assignment rule that assigns the team's open tickets to its members.

## Information kept

- **Name** — the team's name
- **Members** — the agents in the team
- **Ticket access** — whether members see only this team's tickets or every team's tickets while tickets are restricted by team

## States

### Enabled

Routing and access through the team apply, and its rotation runs.

### Disabled

The team's rotation is disabled and the team grants no ticket access.
