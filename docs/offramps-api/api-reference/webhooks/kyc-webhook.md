---
description: Sent whenever there has been a change to the user's KYC status
---

# KYC Webhook

#### Example KYC Update Webhook

```json
{
    "event": "kyc_update",
    "payload": {
        "user": {
            "id": "a25a4274-8f50-4579-b476-8f35b297d4ad",
            "first_name": "Marco",
            "last_name": "Pierre White",
            "email": "marco@cheq.xyz",
            "date_of_birth": "12/12/1985",
            "address_line1": "2 Bellevue Road",
            "address_line2": "Wandsworth Common",
            "city": "London",
            "ssn": null,
            "phone": "+447515772386",
            "beneficiary_type": "individual",
            "nationality": "GB",
            "company_name": null,
            "country": "GB",
            "state": "Berkshire",
            "postcode": "SW177EG",
            "business_description": null,
            "source_of_funds": null,
            "kyc": {
                "general": {
                    "status": "not_started",
                    "moderation_comment": null
                },
                "eur": {
                    "status": "not_started",
                    "swift_status": "not_started"
                },
                "usd": {
                    "status": "not_started",
                    "swift_status": "not_started"
                },
                "ars": {
                    "status": "not_started",
                    "swift_status": "not_started"
                }
            }
        }
    }
}
```
