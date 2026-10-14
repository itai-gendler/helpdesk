---
domain: invitations
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/hooks/user_invitation.py
- kind: code
  role: implementation
  target: helpdesk/overrides/user_invitation.py
- kind: code
  role: implementation
  target: desk/src/components/Settings/InviteAgents.vue
---

# Invitation

An emailed invitation to join the Helpdesk with a role. Accepting an invitation with an agent role makes the person an agent; one with a customer role links them to the inviting customer.

## Information kept

- **Email** — who is invited
- **Role** — Agent, Agent Manager or System Manager for staff; Customer or Customer Manager for contacts
- **Invited by** — who sent the invitation
- **Status** — Pending, Accepted, Expired or Cancelled
