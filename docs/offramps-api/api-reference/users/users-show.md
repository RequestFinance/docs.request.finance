# Users#Show

## Shows a user

#### Example Request

```json
curl https://{{base_url}}/users/USER_ID
-X GET \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json" \
```

#### Endpoint Information

## Shows a User

<mark style="color:blue;">`GET`</mark> `https://{{base_url}}/users/:user_id`

Shows an existing Pay.so user

#### Path Parameters

| Name                                       | Type | Description |
| ------------------------------------------ | ---- | ----------- |
| user\_id<mark style="color:red;">\*</mark> | UUID |             |

{% tabs %}
{% tab title="200: OK " %}
<pre class="language-json"><code class="lang-json">{
    "user": {
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
        "business_activity": null
<strong>        "kyc": {
</strong><strong>            "general": {
</strong><strong>                "status": "not_started",
</strong>                "moderation_comment": null
<strong>            },
</strong>            "eur": {
                "status": "not_started",
                "swift_status": "not_started",
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
</code></pre>
{% endtab %}
{% endtabs %}
