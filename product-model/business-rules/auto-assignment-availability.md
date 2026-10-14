---
appliesTo:
- type: capability-scenario
  id: assign-ticket-by-rule
- type: entity
  id: assignment-rule
  effect: changes
  facts:
  - Last assigned agent
references:
- kind: code
  role: implementation
  target: helpdesk/overrides/assignment_rule.py
---

# Automatic assignment prefers available agents

A rule distributing by rotation or workload picks among its Active assignees; if none is Active, among those Away; only if every assignee is Unavailable, among all of them, so the ticket is never left unassigned for availability alone.
