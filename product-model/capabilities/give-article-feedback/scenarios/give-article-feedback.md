---
kind: primary
routes:
  main: Customer portal
steps:
- text: The Contact marks the Article helpful or not helpful
  kind: actor
  actor: contact
  entities:
  - entity: article
    effect: reads
    facts:
    - Title
  contexts:
    main:
      place: helpdesk-web::customer-portal::article
- text: The Product records or changes the Contact's Article feedback
  kind: product
  actor: contact
  entities:
  - entity: article-feedback
    effect: creates
    facts:
    - Feedback
  contexts:
    main:
      place: helpdesk-web::customer-portal::article
references:
- kind: code
  role: implementation
  target: helpdesk/helpdesk/doctype/hd_article/hd_article.py
---

# Mark an article helpful

## Trigger

A Contact finished reading an Article.

## Outcome

The Article feedback records whether the Contact found it helpful.

## Edge cases

- Choosing the other mark later changes the same feedback; one person keeps one feedback per article.
