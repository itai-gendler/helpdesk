---
appliesTo:
- type: entity
  id: ticket
  effect: changes
  facts:
  - Rating
  - Feedback
  - Feedback comment
permits:
- actors:
  - agent
  - agent-manager
  - system-manager
  - administrator
- related:
  - verb: raises
    entity: contact
  when:
  - fact: Feedback
    absent: true
- related:
  - verb: has
    entity: customer
  - verb: has
    entity: customer-membership
  - verb: holds
    entity: contact
  when:
  - entity: customer-membership
    fact: Role
    is: Customer Manager
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_email_feedback/hd_email_feedback.py
---

# Requesters rate their own ticket once; staff may record a rating

A requester, or a Customer Manager of the ticket's customer, rates a ticket that carries no feedback yet, in the portal or through the feedback link; a rated ticket cannot be rated again by them.
