# PaymentDetails#Index

## Shows all Payment Details belonging to a User

#### Example Request

```json
curl https://{{base_url}}/users/USER_ID/payment_details
-X GET \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json" \
```

#### Endpoint Information

## Shows all Payment Details associated with a User

<mark style="color:blue;">`GET`</mark> `https://{{base_url}}/users/:user_id/payment_details`

#### Path Parameters

| Name                                       | Type | Description                                             |
| ------------------------------------------ | ---- | ------------------------------------------------------- |
| user\_id<mark style="color:red;">\*</mark> | UUID | ID of the User you want to see the Payment Details for. |

{% tabs %}
{% tab title="200: OK " %}
```json
{
    "payment_details": [
        {
            "id": "fa898aec-519c-46be-9b4c-e76ef4ff99d9",
            "user_id": "a25a4274-8f50-4579-b476-8f35b297d4ad",
            "bank_name": "Chase",
            "account_name": "Gordon's Chase Business Account",
            "iban": null",
            "swift_bic": null,
            "beneficiary_type": "business",
            "company_number": "12-3456789",
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
            "rails": "local"
        },
        {
            "id": "576b17c9-db11-4593-a362-52605408a1b5",
            "user_id": "a25a4274-8f50-4579-b476-8f35b297d4ad",
            "bank_name": "Revolut",
            "account_name": "Marco's Revolut",
            "iban": "GB52REVO00997134987725",
            "swift_bic": "REVOGB21",
            "beneficiary_type": "individual",
            "date_of_birth": "12/12/1998",
            "account_number": null,
            "routing_number": null,
            "sort_code": null,
            "document_number": null,
            "account_type": null,
            "currency": "eur",
            "street1": "2 Bellevue Road",
            "street2": "Wandsworth Common",
            "city": "London",
            "state": "London",
            "postal_code": "SW177EG",
            "country": "GB",
            "status": "approved",
            "rails": "swift"
        }
    ]
}
```
{% endtab %}
{% endtabs %}
