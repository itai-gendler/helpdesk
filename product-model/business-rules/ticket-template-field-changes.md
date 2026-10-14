---
appliesTo:
- type: entity
  id: ticket
  effect: changes
  facts:
  - Template fields
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
  - fact: Status
    is-not: Closed
  - fact: Feedback
    absent: true
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
- kind: code
  role: implementation
  target: helpdesk/ticket_fields.py
---

# A requester changes only the template fields left editable after raising

Staff change any template field; a requester, or a Customer Manager of the ticket's customer, changes only the fields the ticket template shows to customers and leaves editable after creation, and never once the ticket is Closed or rated.
