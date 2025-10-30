---
description: Find out how to pay out to one or many bank accounts.
---

# How to make a payment

How to initiate a payment to one or many bank accounts:

1. [Create a Quote object](quotes-create.md). The value of`deposit_token_amount` will initially be 0.
2. [Create an Offramp object](../offramps/offramps-create.md) that belongs to the Quote. This is where you say how much of which currency you want to be delivered to which bank account.
3. You can add one Offramp if you are just paying one bank, or multiple Offramps if you are paying multiple banks in one go.
4. The value of `deposit_token_amount` on the Quote object will increase with every Offramp you add to reflect the amount of crypto that needs to be transferred. You can use Quote#Show to check the value at any time.
5. Once you have added all your Offramps, transfer the `deposit_token_amount` to the provided `deposit_address` and submit the token hash to [Quotes#Execute](quotes-execute.md).
6. You will then receive [webhooks](../webhooks/offramp-webhook.md) informing you about the payment progress.
