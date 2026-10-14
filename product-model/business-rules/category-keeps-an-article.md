---
appliesTo:
- type: capability
  id: delete-article
- type: capability
  id: move-article-to-category
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article/hd_article.py
---

# A category keeps at least one article

Deleting or moving out a category's only article is refused.
