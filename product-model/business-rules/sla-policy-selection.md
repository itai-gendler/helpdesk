---
appliesTo:
- type: capability
  id: raise-ticket
- type: capability
  id: edit-ticket-details
- type: entity
  id: ticket
  effect: changes
  facts:
  - SLA policy
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/utils.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# A ticket follows the first matching enabled policy that covers its priority

Among enabled policies valid today that list the ticket's priority, ranked policies are tried before unranked ones, by rank and then age, and the first whose condition matches applies; the default policy needs no condition but is tried last. With no match the ticket has no SLA timing.

## Rationale

A policy that does not list the ticket's priority never applies, the default included.
