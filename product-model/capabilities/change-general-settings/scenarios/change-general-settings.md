---
kind: primary
routes:
  main: Administration
steps:
- text: The System Manager changes the general settings and saves
  kind: actor
  actor: system-manager
  entities:
  - entity: helpdesk-settings
    effect: reads
    facts:
    - Restrict tickets by team
    - Do not restrict tickets without a team
    - Restrict agent assignment to team
    - Feedback mandatory
    - Comment reactions
    - Auto update status
    - Allow anyone to create tickets
    - Default ticket type
    - Auto-close
    - Auto-close status
    - Auto-close after days
    - Outside working hours notice
    - Outside working hours message
    - Skip email workflow
    - Prefer knowledge base
    - Brand name
    - Logo
    - Favicon
    - Disable global saved replies
  contexts:
    main:
      place: helpdesk-web::administration::general-settings
- text: The Product saves the settings
  kind: product
  actor: system-manager
  entities:
  - entity: helpdesk-settings
    effect: changes
    facts:
    - Restrict tickets by team
    - Do not restrict tickets without a team
    - Restrict agent assignment to team
    - Feedback mandatory
    - Comment reactions
    - Auto update status
    - Allow anyone to create tickets
    - Default ticket type
    - Auto-close
    - Auto-close status
    - Auto-close after days
    - Outside working hours notice
    - Outside working hours message
    - Skip email workflow
    - Prefer knowledge base
    - Brand name
    - Logo
    - Favicon
    - Disable global saved replies
  contexts:
    main:
      place: helpdesk-web::administration::general-settings
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_settings/hd_settings.py
- kind: code
  role: implementation
  target: desk/src/components/Settings/General/components/TicketSettings.vue
---

# Change general settings

## Trigger

A System Manager adjusts how tickets behave.

## Outcome

The settings apply to tickets from then on and every open Helpdesk refreshes them.

## Edge cases

- Auto-close needs a positive number of days.
- Turning on Allow anyone to create tickets lets people who are not signed in create tickets; turning it off withdraws that.
