---
entities:
- entity: ticket
  collects:
  - Rating
  - Feedback comment
entryPoints:
- helpdesk-web: /ticket-feedback/new
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/web_form/email_feedback/email_feedback.json
---

# Rate your support experience

The public feedback form an emailed link opens for one ticket.
