---
appliesTo:
- type: capability
  id: delete-assignment-rule
- type: entity
  id: assignment-rule
  effect: removes
references:
- kind: code
  role: implementation
  target: helpdesk/extends/assignment_rule.py
---

# At least one assignment rule for tickets remains

Deleting the only assignment rule for tickets is refused.
