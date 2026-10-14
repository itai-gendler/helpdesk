---
kind: configuration
of: capability-scenario
settings:
- entity: helpdesk-settings
  fact: Feedback mandatory
takesEffect: When the requester chooses Close. A settings change applies to the next close.
stability: A ticket already closed keeps whatever rating it has.
alternatives:
- id: close-ticket-with-rating
  selectedWhen: Feedback mandatory is on (the default) and an agent has replied on the ticket.
- id: close-ticket-without-rating
  selectedWhen: Feedback mandatory is off, or no agent has replied yet.
---

# Portal close feedback

Closing a ticket in the customer portal either asks for a rating or only for confirmation; the feedback setting and whether an agent has replied choose.
