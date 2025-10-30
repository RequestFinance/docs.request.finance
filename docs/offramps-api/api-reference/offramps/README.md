---
description: The Offramp object represents a fiat payout to a bank account.
---

# Offramps

Once you have created a Quote and made the crypto-transfer to the Quote's deposit address, you'll want to tell us who to pay and how much.\
\
In return, we'll give you an Offramp object for each recipient which tells you the status of the fiat payout.\
\
Below are the possible values for an Offramp's `status`.&#x20;

<table><thead><tr><th width="350">Status</th><th>Description</th></tr></thead><tbody><tr><td>initiated</td><td>The Offramp object has been created but no crypto deposit has yet been received.</td></tr><tr><td>pending_internal_assessment</td><td>The crypto deposit has been received and the payment is awaiting approval from the Request team.</td></tr><tr><td>fiat_sent</td><td>The payment has been sent successfully.</td></tr><tr><td>bounced</td><td>A payment provider has indicated that something has gone wrong with the payment. Either new payment_details must be provided or the user can request a refund.</td></tr><tr><td>failed</td><td>The payment has bounced and funds were refunded to the sender.</td></tr></tbody></table>
