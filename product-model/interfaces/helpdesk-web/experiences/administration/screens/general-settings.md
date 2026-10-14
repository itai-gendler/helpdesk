---
entities:
- entity: helpdesk-settings
  shows: &id001
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
  collects: *id001
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/General/General.vue
---

# General

The Helpdesk's general settings.
