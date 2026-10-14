---
appliesTo:
- type: capability
  id: merge-ticket
- type: capability-scenario
  id: reply-by-email
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/api.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# A ticket merges once, never into itself, and its later replies follow it

Merging needs permission to change both tickets. A merged ticket is Closed and names its target; replies that later arrive on it go to the last unmerged ticket in its merge chain.
