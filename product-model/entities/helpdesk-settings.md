---
singleton: true
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_settings/hd_settings.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_settings/hd_settings.json
---

# Helpdesk settings

The Helpdesk's own settings, kept once for the site: ticket behaviour, team restrictions, email notifications and branding.

## Information kept

- **Restrict tickets by team** — agents see only their teams' tickets, the tickets assigned to them and those they raised
- **Do not restrict tickets without a team** — while tickets are restricted, tickets with no team stay visible to every agent
- **Restrict agent assignment to team** — while tickets are restricted, a ticket's assignees come from its team's members
- **Feedback mandatory** — closing a ticket in the customer portal asks for a rating once an agent has replied
- **Comment reactions** — agents may react to comments with emojis
- **Auto update status** — the status a ticket moves to whenever an agent replies, or none
- **Allow anyone to create tickets** — people who are not signed in may create tickets
- **Default ticket type** — the type a ticket gets when none is chosen
- **Default priority** — the priority a ticket gets when neither its type nor its SLA policy supplies one
- **Default ticket status** — the status a new ticket starts in when its SLA policy names none
- **Reopen status** — the status a requester's reply moves a ticket to when its SLA policy names none
- **Auto-close** — whether stale tickets close automatically
- **Auto-close status** — the status a ticket must be in to close automatically
- **Auto-close after days** — how many days without a message close a ticket automatically
- **Outside working hours notice** — whether a ticket raised outside working hours shows the requester a notice
- **Outside working hours message** — the notice text, which may name the next working day
- **Skip email workflow** — agent replies are kept on the ticket without being emailed
- **Prefer knowledge base** — requesters are guided to articles before raising a ticket
- **Brand name** — the name the Helpdesk shows and uses in invitations
- **Logo** — the brand logo
- **Favicon** — the browser icon
- **Auto-set customer from contact** — a new ticket takes its contact's customer when the contact has exactly one
- **Acknowledgement email** — whether, and with what content, an email-raised ticket's requester is told it was received
- **Reply from contact email** — whether, and with what content, assigned agents are emailed when a requester replies
- **Reply from agent email** — whether, and with what content, agent replies are emailed to the requester
- **Share feedback email** — whether, on which Resolved-category status, and with what content, an email-raised ticket's requester is asked for feedback
- **Disable global saved replies** — while tickets are restricted, saved replies with a global scope are not offered
