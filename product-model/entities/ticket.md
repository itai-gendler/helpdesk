---
domain: tickets
relations:
- entity: reply
  verb: has
  cardinality: one-to-many
- entity: comment
  verb: has
  cardinality: one-to-many
- entity: ticket-activity
  verb: has
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/customer_edit_controller.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.json
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket_status/hd_ticket_status.py
---

# Ticket

A support request raised by a contact or an agent. A ticket carries its conversation of replies, agents' internal comments, a configurable status, its routing (priority, type, team, assignees, customer) and the SLA timing its policy sets.

## Information kept

- **Subject** — the short summary the requester gives
- **Description** — the opening message; set once when the ticket is raised
- **Status** — the configured status the ticket is in; every status belongs to the Open, Paused or Resolved category, and may show customers a label of its own
- **Priority** — one of the configured priorities, such as Urgent, High, Medium or Low
- **Ticket type** — the configured type, which supplies a default priority
- **Team** — the team handling the ticket
- **Raised by** — the email address of whoever raised the ticket
- **Customer** — the customer organization the ticket is for
- **Assigned agents** — the agents working the ticket
- **Raised via portal** — whether the ticket was raised in the Helpdesk rather than by email
- **Raised outside working hours** — whether the ticket arrived on a holiday or outside its SLA policy's working hours
- **Template fields** — the further fields the ticket's template asks for, each visible to agents only or to customers too
- **SLA policy** — the service level agreement that applies to the ticket
- **SLA clock start** — when the policy attached; targets count from here
- **First response due** — when the first response is due
- **Resolution due** — when resolution is due, moved later by time spent paused
- **SLA status** — First Response Due, Resolution Due, Paused, Failed or Fulfilled
- **First responded on** — when the ticket was first answered
- **First response time** — working time from the clock start to the first response
- **Resolution date** — when the ticket entered a Resolved-category status
- **Resolution time** — working time from the clock start to resolution, less hold time
- **On hold since** — when the current pause began
- **Total hold time** — working time the ticket has spent paused
- **Last agent response** — when an agent last replied
- **Last customer response** — when the requester last replied
- **Feedback** — the feedback option chosen when the ticket was rated
- **Rating** — the star rating the requester gave
- **Feedback comment** — the requester's own words about the support
- **Merged with** — the ticket this one was merged into
- **Split from** — the ticket this one was split from
- **Tags** — labels agents put on the ticket; a requester's first ticket is tagged as such

## States

### Open

In a status of the Open category; waiting on the support team, with the SLA clock running.

### Paused

In a status of the Paused category, such as Replied; the SLA clock is on hold.

### Resolved

In a Resolved-category status other than Closed; resolved by an agent and still open to the requester's reply.

### Closed

In the fixed Closed status. Requesters can no longer change it in the portal; a merged ticket is closed.
