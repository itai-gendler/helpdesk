---
kind: primary
routes:
  main: Web
steps:
- text: The Agent Manager enables or disables the email and edits its content
  kind: actor
  actor: agent-manager
  entities:
  - entity: helpdesk-settings
    effect: reads
    facts:
    - Acknowledgement email
    - Reply from contact email
    - Reply from agent email
    - Share feedback email
  contexts:
    main:
      place: helpdesk-web::administration::email-notifications
- text: The Product saves the email
  kind: product
  actor: agent-manager
  entities:
  - entity: helpdesk-settings
    effect: changes
    facts:
    - Acknowledgement email
    - Reply from contact email
    - Reply from agent email
    - Share feedback email
  contexts:
    main:
      place: helpdesk-web::administration::email-notifications
references:
- kind: code
  role: implementation
  target: helpdesk/api/settings/email_notifications.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_settings/hd_settings.py
---

# Change a notification email

## Trigger

An Agent Manager edits a notification email.

## Outcome

The email is sent, or not, with the new content from then on.

## Edge cases

- Content that is not a valid template is refused.
- The share feedback email must be sent on a Resolved-category status.
