---
domain: assignment-rules
references:
- kind: code
  role: implementation
  target: helpdesk/overrides/assignment_rule.py
- kind: code
  role: implementation
  target: helpdesk/extends/assignment_rule.py
- kind: code
  role: implementation
  target: desk/src/components/Settings/Assignment Rules/AssignmentRuleView.vue
---

# Assignment rule

A rule that assigns tickets automatically: while enabled and on its active days, a ticket that matches its assignment condition goes to one of its assignees by its routing, and one that matches its unassignment condition loses that assignment.

## Information kept

- **Name** — the rule's name
- **Description** — what the rule is for
- **Priority** — Low to High; higher-priority rules are tried first
- **Assignment condition** — which tickets the rule assigns
- **Unassignment condition** — which tickets lose the rule's assignment
- **Assignment days** — the weekdays the rule is active
- **Routing** — Auto-rotate or Assign by workload
- **Assignees** — the agents tickets are distributed among
- **Last assigned agent** — the agent the rule assigned most recently

## States

### Enabled

The rule assigns and unassigns tickets.

### Disabled

The rule is ignored.
