# PaymentDetails#Deactivate

## Deactivate a Payment Detail

#### Example Request

```json
curl https://{{base_url}}/users/USER_ID/payment_details/PAYMENT_DETAIL_ID/deactivate
-X PATCH \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json" \
```

#### Endpoint Information

## Deactivate a Payment Detail

<mark style="color:purple;">`PATCH`</mark> `https://{{base_url}}/users/:user_id/payment_details/:payment_detail_id/deactivate`

#### Path Parameters

| Name                                                  | Type | Description                                         |
| ----------------------------------------------------- | ---- | --------------------------------------------------- |
| user\_id<mark style="color:red;">\*</mark>            | UUID | ID of the User which the Payment Detail belongs to. |
| payment\_detail\_id<mark style="color:red;">\*</mark> | UUID | ID of the Payment Detail you wish to deactivate.    |

{% tabs %}
{% tab title="200: OK " %}
```json
{
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
            "status": "deactivated",
            "rails": null
        }
}
```
{% endtab %}
{% endtabs %}
