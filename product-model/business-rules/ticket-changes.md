---
appliesTo:
- type: entity
  id: ticket
  effect: changes
permits:
- related:
  - verb: raises
    entity: contact
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
- actors:
  - administrator
- unattended: true
- actors:
  - agent
  - agent-manager
  - system-manager
  when:
  - entity: helpdesk-settings
    fact: Restrict tickets by team
    is: 'Off'
- related:
  - verb: is assigned to
    entity: agent
- related:
  - verb: handles
    entity: team
  - verb: includes
    entity: agent
- actors:
  - agent
  - agent-manager
  - system-manager
  when:
  - entity: helpdesk-settings
    fact: Do not restrict tickets without a team
    is: 'On'
  - fact: Team
    absent: true
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
---

# Whoever may read a ticket may work on it, within the narrower ticket rules

The same people who read a ticket may change it — its requester, the Customer Managers of its customer, the agents its team restriction admits and the Administrator — and the Product updates it on its own schedules; the rules on routing fields, statuses, template fields and ratings narrow what requesters may change.
