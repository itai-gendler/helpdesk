---
domain: knowledge-base
relations:
- entity: article-feedback
  verb: has
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article/hd_article.py
- kind: code
  role: implementation
  target: helpdesk/api/knowledge_base.py
---

# Article

A help article in the knowledge base. Agents write and publish articles; requesters read the published ones, and articles matching a new ticket's subject are suggested while it is written.

## Information kept

- **Title** — the article's title
- **Content** — the article body; a published article always has content
- **Category** — the category it is filed in
- **Author** — the agent who created it
- **Published on** — when it was published
- **Views** — how many times requesters opened it

## States

### Draft

Visible to agents only.

### Published

Visible to requesters in the knowledge base.
