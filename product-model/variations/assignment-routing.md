---
kind: configuration
of: business-rule
settings:
- entity: assignment-rule
  fact: Routing
takesEffect: Each time the rule assigns a ticket. A routing change applies to the next assignment.
stability: Tickets already assigned keep their assignees.
alternatives:
- id: round-robin-routing
  selectedWhen: Routing is Auto-rotate, the default for a new rule.
- id: load-balancing-routing
  selectedWhen: Routing is Assign by workload.
---

# Assignment routing

Each assignment rule distributes its tickets either in rotation or by workload; both policies are supported and the rule's routing chooses.
