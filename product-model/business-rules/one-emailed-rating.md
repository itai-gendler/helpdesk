---
appliesTo:
- type: capability
  id: share-ticket-feedback
- type: entity
  id: ticket
  effect: changes
  facts:
  - Rating
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_email_feedback/hd_email_feedback.py
---

# A ticket takes one rating through its feedback link

The feedback link carries a key unique to the ticket; a second submission for the same key is refused, and the rating closes the ticket.
