---
appliesTo:
- type: entity
  id: comment
  effect: changes
  facts:
  - Reactions
permits:
- actors:
  - agent
  - agent-manager
  - system-manager
  - administrator
  when:
  - entity: helpdesk-settings
    fact: Comment reactions
    is: 'On'
references:
- kind: code
  role: implementation
  target: helpdesk/api/comment.py
---

# Agents react to comments while reactions are enabled

Only the preset emojis are allowed, and each agent keeps one reaction per comment.
