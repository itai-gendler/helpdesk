---
id: helpdesk
summary: Open-source ticket management with agent and customer portals, SLA policies, assignment rules and email intake.
category: customer-support
tags:
- helpdesk
- ticketing
- sla
- customer-portal
authors:
- name: Frappe Technologies
  url: https://frappe.io
license: AGPL-3.0-only
languages:
- en
- ar
- bg
- bs
- cs
- da
- de
- eo
- es
- fa
- fr
- hi
- hr
- hu
- id
- it
- ko
- my
- nb
- nl
- pl
- pt
- pt-BR
- ru
- sl
- sr
- sr-CS
- sv
- ta
- th
- tr
- uz
- vi
- zh
limitations:
- Ticket statuses, ticket types and priorities are configured in the Frappe desk, not in the Helpdesk's own settings.
- Customers close tickets but never resolve them; resolving is an agent's call.
- Only the site's Administrator account deletes tickets.
- Outgoing and incoming email run through the site's email accounts; the Helpdesk sends no mail of its own.
- SLA targets count only the working hours and holidays of the ticket's policy.
references:
- kind: code
  role: implementation
  target: README.md
- kind: code
  role: implementation
  target: helpdesk/hooks.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
---

# Helpdesk

Frappe Helpdesk is a ticket management product for support teams. Requesters raise tickets by email or in the customer portal; agents answer them in the agent portal, where each ticket carries a configurable status, a priority, a team, assignees and the service level agreement (SLA) that sets its first-response and resolution targets. Agent Managers configure SLA policies with working hours and business holidays, teams and the assignment rules that route tickets, customers and their contacts, and the agents themselves.

## Intent

Make customer service simple and effective: a fully open-source ticket management tool that streamlines a company's support, with an easy setup, a clean interface and automation tools — dual agent and customer portals, customizable SLAs and assignment rules based on priority, issue type or workload — so customer queries are resolved efficiently. It was built to replace a support module whose interface and experience fell short, and to integrate with and be customized for an existing system.
