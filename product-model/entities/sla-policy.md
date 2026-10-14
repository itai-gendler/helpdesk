---
domain: sla-policies
relations:
- entity: ticket
  verb: governs
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/hd_service_level_agreement.py
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_service_level_agreement/utils.py
---

# SLA policy

A service level agreement: which tickets it covers, the first-response and resolution targets for each priority, the working hours and holiday list targets count in, and the statuses its tickets start and reopen in.

## Information kept

- **Name** — the policy's name, fixed once created
- **Description** — what the policy is for
- **Default** — whether this is the default policy, applied when no other matches
- **Rank** — the order matching policies are tried in; 0 is unranked and tried last
- **Condition** — which tickets the policy covers
- **Valid from** — the first day the policy applies
- **Valid to** — the last day the policy applies
- **Priority targets** — for each covered priority, the first response time and resolution time; one priority is the default
- **Apply to resolution** — whether the policy also sets a resolution target
- **Working hours** — for each working weekday, the start and end of working time
- **Holiday list** — the holiday list whose days are not working time
- **Default ticket status** — the status its new tickets start in
- **Reopen status** — the status a requester's reply moves its tickets to

## States

### Enabled

The policy can apply to tickets.

### Disabled

The policy applies to no ticket; tickets on it lose it the next time they change unless another policy matches.
