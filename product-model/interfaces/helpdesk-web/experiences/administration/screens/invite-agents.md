---
entities:
- entity: invitation
  shows:
  - Email
  - Role
  - Invited by
  - Status
  collects:
  - Email
  - Role
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/InviteAgents.vue
---

# Invite Agents

Inviting agents and the pending invitations.
