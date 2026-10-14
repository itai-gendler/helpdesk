---
appliesTo:
- type: entity
  id: reply
  effect: creates
  contexts:
  - place: helpdesk-web::customer-portal
permits:
- related:
  - verb: has
    entity: ticket
  - verb: raises
    entity: contact
  when:
  - entity: ticket
    fact: Status
    is-not: Closed
  - entity: ticket
    fact: Feedback
    absent: true
- related:
  - verb: has
    entity: ticket
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
  - entity: ticket
    fact: Status
    is-not: Closed
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
- kind: code
  role: implementation
  target: desk/src/pages/ticket/TicketCustomer.vue
---

# A requester replies in the portal while the ticket is open to them

A requester, or a Customer Manager of the ticket's customer, replies in the customer portal until the ticket is Closed or rated.
