# Users#Index

## Fetches all Users associated with your Organization

#### Example Request

```json
curl https://{{base_url}}/users
-X GET \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json" \
```

#### Endpoint Information

## Fetches all users

<mark style="color:blue;">`GET`</mark> `https://{{base_url}}/users`

Fetches all users associated with your organization account

{% tabs %}
{% tab title="200: OK " %}
```json
{
    "users": [
        {
            "id": "a25a4274-8f50-4579-b476-8f35b297d4ad",
            "beneficiary_type": "individual",
            "first_name": "Marco",
            "last_name": "Pierre White",
            "company_name": null,
            "email": "marco@cheq.xyz",
            "date_of_birth": "12/12/1985",
            "address_line1": "2 Bellevue Road",
            "address_line2": "Wandsworth Common",
            "city": "London",
            "state": "London",
            "postcode": "SW177EG",
            "country": "GB",
            "nationality": "GB",
            "ssn": null,
            "source_of_funds": null,
            "business_activity": null,
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
    ]
}
```
{% endtab %}
{% endtabs %}
