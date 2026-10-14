---
appliesTo:
- type: entity
  id: ticket
  effect: reads
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
  target: helpdesk/utils.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py#permission_query
---

# Requesters, their Customer Managers and permitted agents read a ticket

A contact reads the tickets they raised, and a Customer Manager every ticket of the customers they manage. Agents read every ticket unless Restrict tickets by team is on; then an agent reads the tickets of their enabled teams, tickets assigned to them, and — when Do not restrict tickets without a team is on — tickets with no team. A member of a team whose ticket access is all team tickets reads every team's tickets. The Administrator reads every ticket.
