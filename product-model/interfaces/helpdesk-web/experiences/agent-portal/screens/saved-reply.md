---
entities:
- entity: saved-reply
  shows: &id001
  - Title
  - Message
  - Scope
  - Teams
  - Actions
  collects: *id001
- entity: team
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: desk/src/components/Settings/SavedReplies/SavedReplyView.vue
---

# Saved reply

Creating or editing one saved reply.
