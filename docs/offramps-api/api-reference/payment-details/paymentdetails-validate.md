# PaymentDetails#Validate

## Validate a Payment Detail

This endpoint can determine whether the provided payment detail will pass regex checks.

\
NB: It does not guarantee it will be accepted by our payment partners. Nor does it guarantee it will be the recipients intended account.&#x20;

#### Example Request

```json
curl https://{{base_url}}/users/USER_ID/payment_details/validate
-X POST \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json" \
-d '{
    "payment_detail": {
        "bank_name": "Chase",
        "account_name": "Gordon's Chase Business Account",
        "account_number": "253009233489",
        "routing_number": "026013356",
        "beneficiary_type": "business",
        "company_number": "12-3456789",
        "currency": "usd",
        "address_line1": "24 Theatre St.",
        "city": "Paramount",
        "state": "CA",
        "country": "US",
        "postal_code": "90723",
        "rails": null
    }
}'
```

#### Endpoint Information

## Validate Payment Detail Parameters

<mark style="color:green;">`POST`</mark> `https://{{base_url}}/users/:user_id/payment_details/validate`

#### Path Parameters

| Name                                       | Type | Description                                         |
| ------------------------------------------ | ---- | --------------------------------------------------- |
| user\_id<mark style="color:red;">\*</mark> | UUID | ID of the User which the Payment Detail belongs to. |

#### Request Body

| Name                       | Type   | Description                                                                                                                                                                                                                                       |
| -------------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| account\_name              | String | A name to identify the bank account, e.g. 'Chris's Revolut'.                                                                                                                                                                                      |
| account\_number            | String | The account number of the bank account. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                 |
| currency                   | String | The currency that the bank account accepts. E.g. 'usd', 'eur'.                                                                                                                                                                                    |
| address\_line1             | String | The first line of the address of the person or organisation that controls the bank account.                                                                                                                                                       |
| address\_line2             | String | The second line of the address of the person or organisation that controls the bank account.                                                                                                                                                      |
| city                       | String | The city where the person or organisation that controls the bank account is located.                                                                                                                                                              |
| state                      | String | The state/district where the person or organisation that controls the bank account is located.                                                                                                                                                    |
| postal\_code               | String | The postal/zip code where the person or organisation that controls the bank account is located.                                                                                                                                                   |
| country                    | String | The country where the person or organisation that controls the bank account is located. Given in ISO 3166-1 alpha-2 format.                                                                                                                       |
| beneficiary\_type          | String | `individual` or `business`                                                                                                                                                                                                                        |
| routing\_number            | String | The ACH routing number of the bank account. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                             |
| bank\_name                 | String | The name of the bank associated with the account. e.g. 'Revolut'                                                                                                                                                                                  |
| sort\_code                 | String | The sort code of the bank account. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                      |
| iban                       | String | The IBAN of the bank account. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                           |
| swift\_bic                 | String | The swift/bic of the bank account. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                      |
| document\_number           | String | The recipient's CUIT (tax number). See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                      |
| account\_type              | String | `checking` or `savings`. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                                |
| rib\_number                | String | The recipient's Relevé d'Identité Bancaire number. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                      |
| purpose\_of\_transfer      | String | Explanation of what the purpose of the transfer is. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                     |
| purpose\_of\_payment\_code | String | Code describing the purpose of the payment. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                             |
| bsb\_number                | String | The recipient's BSB number. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                             |
| rails                      | String | If the account is on the SWIFT network, put the value of this attribute to`swift`. Otherwise if it is SEPA/ACH or other local rails you can leave it as `null`. Please see [SWIFT Support](rail-availability.md) to understand what is supported. |

{% tabs %}
{% tab title="200: OK " %}
```json
{
    "payment_detail": {
        "valid": true,
        "errors": []
    }
}
```
{% endtab %}
{% endtabs %}

