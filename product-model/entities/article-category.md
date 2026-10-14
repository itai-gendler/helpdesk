---
domain: knowledge-base
relations:
- entity: article
  verb: files
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article_category/hd_article_category.py
- kind: code
  role: implementation
  target: helpdesk/api/knowledge_base.py
---

# Category

A knowledge base category articles are filed in. The General category always exists, keeps its name and cannot be deleted or merged away.

## Information kept

- **Name** — the category's name; General is reserved
- **Description** — what the category covers
