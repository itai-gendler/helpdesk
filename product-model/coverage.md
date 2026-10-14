---
scope: 'The Helpdesk app: ticket intake, conversation, routing, SLA, portals, knowledge base, saved replies, customers, contacts and administration settings.'
method: Static inspection of backend doctypes, APIs, hooks and the Vue SPA; tests read as leads.
covered:
- description: Ticket doctype, its API, customer edit guard and ticket field rules
  paths:
  - helpdesk/helpdesk/doctype/hd_ticket/
  - helpdesk/ticket_fields.py
  - helpdesk/consts.py
  - helpdesk/api/ticket.py
  - helpdesk/api/tags.py
  - helpdesk/api/doc.py
- description: SLA policies, priorities, working days and holiday lists
  paths:
  - helpdesk/helpdesk/doctype/hd_service_level_agreement/
  - helpdesk/helpdesk/doctype/hd_service_level_priority/
  - helpdesk/helpdesk/doctype/hd_service_day/
  - helpdesk/helpdesk/doctype/hd_service_holiday_list/
  - helpdesk/helpdesk/doctype/hd_holiday/
- description: Teams, agents, agent statuses and assignment rule overrides
  paths:
  - helpdesk/helpdesk/doctype/hd_team/
  - helpdesk/helpdesk/doctype/hd_team_member/
  - helpdesk/helpdesk/doctype/hd_agent/
  - helpdesk/helpdesk/doctype/hd_agent_status/
  - helpdesk/overrides/assignment_rule.py
  - helpdesk/extends/assignment_rule.py
  - helpdesk/api/assignment_rule.py
- description: Customers, contacts, memberships and invitations
  paths:
  - helpdesk/helpdesk/doctype/hd_customer/
  - helpdesk/helpdesk/doctype/hd_customer_member/
  - helpdesk/api/customer.py
  - helpdesk/api/contact.py
  - helpdesk/helpdesk/hooks/
  - helpdesk/overrides/user_invitation.py
- description: Ticket comments, reactions, notifications, email feedback and inbound email handling
  paths:
  - helpdesk/extends/comment.py
  - helpdesk/api/comment.py
  - helpdesk/helpdesk/doctype/hd_comment_reaction/
  - helpdesk/notifications.py
  - helpdesk/extends/notification_log.py
  - helpdesk/helpdesk/doctype/hd_email_feedback/
  - helpdesk/helpdesk/web_form/
  - helpdesk/overrides/email_account.py
- description: Knowledge base articles, categories, feedback and article search
  paths:
  - helpdesk/helpdesk/doctype/hd_article/
  - helpdesk/helpdesk/doctype/hd_article_category/
  - helpdesk/helpdesk/doctype/hd_article_feedback/
  - helpdesk/api/knowledge_base.py
  - helpdesk/api/article.py
  - desk/src/pages/knowledge-base/
  - desk/src/components/knowledge-base/
- description: Saved replies, their scopes and actions
  paths:
  - helpdesk/helpdesk/doctype/hd_saved_reply/
  - helpdesk/helpdesk/doctype/hd_saved_reply_team/
  - helpdesk/api/saved_replies.py
  - desk/src/components/Settings/SavedReplies/
- description: Helpdesk settings, email account and email notification settings
  paths:
  - helpdesk/helpdesk/doctype/hd_settings/
  - helpdesk/api/settings/email_notifications.py
  - helpdesk/api/settings/email.py
  - desk/src/components/Settings/EmailNotifications/
  - desk/src/components/Settings/EmailAdd.vue
  - desk/src/components/Settings/EmailEdit.vue
  - desk/src/components/Settings/EmailAccountList.vue
- description: Dashboard, agent home and agent search
  paths:
  - helpdesk/api/dashboard.py
  - helpdesk/api/agent_home/
  - helpdesk/api/search.py
  - helpdesk/search_sqlite.py
  - desk/src/pages/dashboard/
  - desk/src/pages/home/
  - desk/src/pages/SearchAgent.vue
- description: Shared permission helpers, hooks, install defaults and auth
  paths:
  - helpdesk/utils.py
  - helpdesk/hooks.py
  - helpdesk/setup/install.py
  - helpdesk/setup/comments.py
  - helpdesk/api/auth.py
- description: SPA routing, ticket, customer, contact and notification pages and the mapped settings screens
  paths:
  - desk/src/router/
  - desk/src/pages/ticket/
  - desk/src/pages/customer/
  - desk/src/pages/contact/
  - desk/src/pages/MobileNotifications.vue
  - desk/src/components/ticket-agent/
  - desk/src/components/ticket/
  - desk/src/components/customer/
  - desk/src/components/contact/
  - desk/src/components/notifications/
  - desk/src/components/Settings/Sla/
  - desk/src/components/Settings/Holiday/
  - desk/src/components/Settings/Teams/
  - desk/src/components/Settings/Assignment Rules/
  - desk/src/components/Settings/General/
  - desk/src/components/Settings/Agents.vue
  - desk/src/components/Settings/InviteAgents.vue
exclusions:
- description: Translations, assets, icons and styling
  paths:
  - helpdesk/locale/
  - desk/src/assets/
  - desk/src/components/icons/
  - helpdesk/public/
- description: Tests, end-to-end suites and CI
  paths:
  - helpdesk/tests/
  - e2e/
  - .github/
- description: Data migrations, upgrade notices and deployment tooling
  paths:
  - helpdesk/patches/
  - docker/
  - helpdesk/api/banners.py
  - helpdesk/api/customer_portal_notice.py
  - desk/src/components/banners/
- description: Telemetry, onboarding and the persona questionnaire
  paths:
  - desk/src/telemetry.ts
  - helpdesk/api/onboarding.py
  - desk/src/pages/PersonaForm.vue
  - desk/src/persona.ts
- description: Telephony and call logs, provided by the separate Telephony app
  paths:
  - desk/src/components/Settings/Telephony/
  - desk/src/pages/call-logs/
  - desk/src/components/telephony/
- description: ERPNext integration, owned by ERPNext
  paths:
  - helpdesk/integrations/
  - desk/src/components/erpnext-integration/
  - helpdesk/helpdesk/doctype/erpnext_hd_settings/
- description: Desk reports and form scripts, developer customization in the Frappe desk
  paths:
  - helpdesk/helpdesk/report/
  - helpdesk/helpdesk/doctype/hd_form_script/
- description: Command palette, a navigation shortcut over mapped behavior
  paths:
  - desk/src/components/command-palette/
unmapped:
- description: Ticket status, type, priority and feedback option records, configured in the Frappe desk rather than the Helpdesk app
  paths:
  - helpdesk/helpdesk/doctype/hd_ticket_status/
  - helpdesk/helpdesk/doctype/hd_ticket_type/
  - helpdesk/helpdesk/doctype/hd_ticket_priority/
  - helpdesk/helpdesk/doctype/hd_ticket_feedback_option/
- description: Ticket templates, field layouts and field dependencies, form customization summarized by the ticket's template fields
  paths:
  - helpdesk/helpdesk/doctype/hd_ticket_template/
  - helpdesk/helpdesk/doctype/hd_ticket_template_field/
  - helpdesk/helpdesk/doctype/hd_field_layout/
  - helpdesk/api/settings/field_dependency.py
  - desk/src/components/Settings/FieldDependency/
- description: Saved list views, a personalization of browsing tickets
  paths:
  - helpdesk/helpdesk/doctype/hd_view/
  - desk/src/components/view-controls/
- description: Personal profile and preference settings kept on the framework user
  paths:
  - desk/src/components/Settings/Profile/
  - desk/src/components/Settings/Preferences/
limitations:
- description: Frappe framework assignment, email intake and invitation behaviour the app relies on but does not contain
  paths:
  - helpdesk/overrides/assignment_rule.py
  - helpdesk/overrides/email_account.py
  - helpdesk/helpdesk/hooks/user_invitation.py
---

# Coverage
