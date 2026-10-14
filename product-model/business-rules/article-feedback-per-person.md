---
appliesTo:
- type: entity
  id: article-feedback
  effect: creates
permits:
- actors:
  - contact
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article/hd_article.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article_feedback/hd_article_feedback.json
---

# Each requester keeps one feedback per article

Marking again changes the requester's existing feedback.
