---
description: Sent whenever there has been a change to an Offramp object
---

# Offramp Webhook

#### Example Offramp Update Webhook

```json
{
    "event": "offramp_update",
    "payload": {
       "offramp": {
          "id": "074cb3e4-1f56-4916-8024-ecbf6f805b90",
          "user_id": "a25a4274-8f50-4579-b476-8f35b297d4ad",
          "payment_detail_id": "fa898aec-519c-46be-9b4c-e76ef4ff99d9",
          "quote_id": "1e99d470-dcc2-46f4-970c-bc35a9e13b84",
          "status": "initiated",
          "status_message": null,
          "destination_amount": 19000,
          "destination_currency": "usd",
          "reference": "Payment for Services #1010",
          "rails": "swift",
          "rate": 0.92820,
          "fee": 125,
          "supporting_document": {
              "submitted_url": "https://web3accounting.com/invoices/in_378949x.pdf",
              "status": "not_checked"
          }
       }
    }
}
```
