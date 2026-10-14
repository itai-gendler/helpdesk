---
appliesTo:
- type: capability
  id: publish-article
- type: entity
  id: article
  effect: changes
  to: Published
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article/hd_article.py
---

# A published article has content

Publishing an article without content is refused.
