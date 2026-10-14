---
appliesTo:
- type: entity
  id: saved-reply
  effect: reads
permits:
- actors:
  - agent-manager
  - system-manager
  - administrator
  when:
  - fact: Scope
    is-not: Personal
- actors:
  - agent
  when:
  - fact: Scope
    is: Global
  - entity: helpdesk-settings
    fact: Disable global saved replies
    is: 'Off'
- actors:
  - agent
  when:
  - fact: Scope
    is: Team
  - entity: helpdesk-settings
    fact: Restrict tickets by team
    is: 'Off'
- related:
  - verb: shares
    entity: team
  - verb: includes
    entity: agent
  when:
  - fact: Scope
    is: Team
- related:
  - verb: writes
    entity: agent
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_saved_reply/hd_saved_reply.py
---

# Agents see their own, their teams' and global saved replies

An agent sees their personal saved replies, global ones unless Disable global saved replies is on while tickets are restricted, and team ones — all of them, or while tickets are restricted by team only those shared with their teams. Agent Managers and System Managers see every shared saved reply.
