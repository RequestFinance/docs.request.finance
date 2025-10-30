---
description: >-
  Payment Details are bank accounts to which your users can have fiat currency
  paid out into.
---

# Payment Details

Upon creation of a Payment Detail, the `status` field might be one of the following: `approved`, `failed`, `pending`.\
\
Approved means the user is clear to start making Offramps to the bank account. Failed means the account has been rejected by us or our partners and the user won't be able to pay to it. Pending means it is undergoing review.\
\
Changes to a Payment Detail's status field will be relayed to you as a webhook.
