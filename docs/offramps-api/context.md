---
description: How to integrate and authenticate with the Request Technology service.
---

# Getting Started

### Onboarding a User

Below is a step-by-step overview on how to register a user and complete their first crypto-to-fiat payment.

1. Collect user details and [create the User object](api-reference/users/#creating-a-user) in Core. Have them sign the usage [agreement](api-reference/agreements/agreements-show.md).
2. [Create a KYC Session](api-reference/kyc-sessions/#creating-a-kyc-session) and ask the user to follow and complete the onboarding URL.
3. Wait for a [webhook](api-reference/webhooks/#example-kyc-update) to arrive confirming the user has been approved. (Note: in sandbox you can manually update their approval status [via our special moves endpoints](sandbox-only/sandbox-special-moves.md)).

### Performing an Offramp

1. Collect the details of the recipient bank account and [create a Payment Detail object](api-reference/payment-details/#create-a-payment-detail).
2. [Create a Quote](api-reference/quotes/quotes-create.md). This object will update after you complete step 3 to tell you how much crypto to send and where.
3. [Create Offramp objec](api-reference/offramps/offramps-create.md)[ts](api-reference/offramps/offramps-create.md) that tell us which bank accounts we should send fiat to once your Quote is executed.
4. [Execute your Quote](api-reference/quotes/quotes-execute.md) to begin the fiat processing.
5. Await [webhook](broken-reference) with updates regarding the progress of each Offramp.

### Base URL

The base URL is where our API is hosted. While you are developing we recommend using our sandbox (staging) domain before switching onto production. Throughout our documentation it will be referred to as `{{base_url}}`

#### Sandbox Base URL

`https://core-api-staging.pay.so/v1`

#### Production Base URL

`https://core-api.pay.so/v1`
