---
availability:
- place: helpdesk-web::administration
domain: agents
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/agents.ts
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_agent/hd_agent.py
- kind: code
  role: implementation
  target: helpdesk/utils.py
---

# Disable agent

Take agent access away from an agent while keeping their record.
