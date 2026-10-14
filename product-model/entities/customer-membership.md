---
domain: customers
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_customer/hd_customer.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/hooks/user_invitation.py
---

# Customer membership

A contact's place in a customer. The membership's role decides whether the contact also sees and manages the customer's tickets.

## Information kept

- **Role** — Customer or Customer Manager
