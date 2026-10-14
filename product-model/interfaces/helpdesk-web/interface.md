---
type: web
actors:
- contact
- agent
- agent-manager
- system-manager
- administrator
entryPoints:
- web: /helpdesk
- support-email: /helpdesk/my-tickets/:ticketId
- support-email: /ticket-feedback/new?key=:key
references:
- kind: code
  role: implementation
  target: desk/src/router/index.ts
- kind: code
  role: implementation
  target: helpdesk/www/helpdesk/index.py
---

# Helpdesk web app

The single-page web app served under `/helpdesk`, with a customer portal for requesters, an agent portal for support staff and an administration area in its settings, plus the public page an emailed feedback link opens. People sign in through the site's login page; a signed-in person without agent access is sent to the customer portal.
