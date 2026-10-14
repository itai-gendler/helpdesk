---
appliesTo:
- type: capability
  id: view-dashboard
- type: capability
  id: view-home
references:
- kind: code
  role: implementation
  target: helpdesk/api/dashboard.py
- kind: code
  role: implementation
  target: helpdesk/api/agent_home/agent_home.py
---

# Agents see only their own dashboard figures; Agent Managers see everyone's

Asking for another agent's or a team's figures without being an Agent Manager is refused.
