---
appliesTo:
- type: capability-scenario
  id: reply-with-saved-reply
- type: entity
  id: saved-reply
  facts:
  - Actions
references:
- kind: code
  role: implementation
  target: helpdesk/api/saved_replies.py
---

# Saved reply actions apply only after the reply is sent

A saved reply's actions change the ticket after its reply is out, skipping and reporting any that are no longer valid; an explicit assignment wins over the team-change cleanup.
