---
description: >-
  Due to regulatory requirements, Request Technologies UAB requires the
  identification of originator and beneficiary ("Travel Rule")
---

# Travel Rule

To comply with global anti-money laundering (AML) regulations, specifically the Travel Rule (see [https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32023R1113](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32023R1113)), Request Technologies UAB must collect a set of information about the sender and the receiver of all offramps. This includes **verifying the ownership of unhosted** **wallets** (i.e. self-custody wallets like MetaMask, Ledger, etc.).

To ease your users' experience, we use [Sumsub](https://sumsub.com/) to verify ownership of unhosted wallets used for payments. The process ensures the wallet belongs to your user and can be used for payouts. Users only need to verify new wallets once.&#x20;

Whenever an offramp is made, a validation is run whether the wallet requires ownership verification or not. If verification is required, we'll send a webhook (see [Travel Rule webhook](./)) with an ID you can use to retrieve the [verification link](retrieving-unhosted-wallet-verification-link.md)

The webhook also notifies you of any status changes in the wallet ownership verification.&#x20;

**Possible Status Values**

| Status   | Value      |
| -------- | ---------- |
| Approved | `approved` |
| On Hold  | `onHold`   |
| Rejected | `rejected` |
