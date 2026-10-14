---
domain: saved-replies
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_saved_reply/hd_saved_reply.py
- kind: code
  role: implementation
  target: helpdesk/api/saved_replies.py
---

# Saved reply

A reusable reply text agents insert while replying, rendered with the ticket's details. It may carry actions applied to the ticket once the reply is sent: set status, priority, team or type, assign, tag, or comment.

## Information kept

- **Title** — the saved reply's name
- **Message** — the reply text, which may use the ticket's and the agent's details
- **Scope** — Personal, Team or Global
- **Teams** — the teams a Team-scoped reply is shared with
- **Actions** — changes applied to the ticket after the reply is sent; at most one assignment, no tag both added and removed
- **Author** — the agent who created it
