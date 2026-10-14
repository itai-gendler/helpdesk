---
kind: person
acts: external
relations:
- entity: ticket
  verb: raises
  cardinality: one-to-many
- entity: customer-membership
  verb: holds
  cardinality: one-to-many
- entity: article-feedback
  verb: gives
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_ticket/hd_ticket.py
- kind: code
  role: implementation
  target: helpdesk/api/contact.py
---

# Contact

A person who asks for support. A contact raises tickets by email or, with a portal account, in the customer portal, and follows and replies to the tickets they raised. Agents add contacts to customers; a contact who belongs to a customer as its Customer Manager also sees every ticket of that customer.

## Information kept

- **Name** — first and last name
- **Email** — the addresses a contact's emails and tickets are matched by, one of them primary
- **Phone** — phone numbers, one of them primary
- **Image** — the contact's picture
- **Portal account** — whether the contact has a user to sign in to the customer portal
