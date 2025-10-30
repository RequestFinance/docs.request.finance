---
description: Sent whenever there has been a update to the status of a Payment Detail
---

# Payment Detail Webhook

**Example Payment Detail Update Webhook**

```json
{
    "event": "payment_detail_update",
    "payload": {
        "payment_detail": {
            "id": "fa898aec-519c-46be-9b4c-e76ef4ff99d9",
            "user_id": "a25a4274-8f50-4579-b476-8f35b297d4ad",
            "bank_name": "Chase",
            "account_name": "Gordon's Chase Business Account",
            "iban": null",
            "swift_bic": null,
            "beneficiary_type": "business",
            "account_number": "253009233489",
            "routing_number": "026013356",
            "sort_code": null,
            "document_number": null,
            "account_type": null,
            "currency": "usd",
            "address_line1": "24 Theatre St.",
            "address_line2": null,
            "city": "Paramount",
            "state": "CA",
            "postal_code": "90723",
            "country": "US",
            "status": "approved",
            "rails": null
        }
    }
}
```

**Possible Status Values**

| Status      | Value         |
| ----------- | ------------- |
| Initiated   | `initiated`   |
| Approved    | `approved`    |
| Pending     | `pending`     |
| Failed      | `failed`      |
| Deactivated | `deactivated` |
