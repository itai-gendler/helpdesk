---
availability:
- place: helpdesk-web::customer-portal
- place: helpdesk-web::agent-portal
domain: knowledge-base
references:
- kind: code
  role: implementation
  target: helpdesk/api/knowledge_base.py
- kind: code
  role: implementation
  target: desk/src/pages/knowledge-base/KnowledgeBaseCustomer.vue
- kind: code
  role: implementation
  target: desk/src/pages/knowledge-base/KnowledgeBaseAgent.vue
- kind: code
  role: implementation
  target: helpdesk/api/article.py
---

# Browse knowledge base

Find and read help articles by category or search: requesters see published articles in the customer portal; agents see every article in the agent portal.
