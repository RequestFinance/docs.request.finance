# PaymentDetails#Create

## Create a Payment Detail

NB: For a list of what fields are required per currency, see [Required Fields For Currencies](required-fields-for-currencies.md).

#### Example Request

```json
curl https://{{base_url}}/users/USER_ID/payment_details
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
        "currency": "usd",
        "address_line1": "24 Theatre St.",
        "city": "Paramount",
        "state": "CA",
        "country": "US",
        "date_of_birth": "12/12/1985",
        "postal_code": "90723",
        "rails": "local"
    }
}'
```

#### Endpoint Information

## Create a Payment Detail

<mark style="color:green;">`POST`</mark> `https://{{base_url}}/users/:user_id/payment_details`

#### Path Parameters

| Name                                       | Type   | Description                                         |
| ------------------------------------------ | ------ | --------------------------------------------------- |
| user\_id<mark style="color:red;">\*</mark> | UUID   | ID of the User which the Payment Detail belongs to. |
|                                            | String |                                                     |

#### Request Body

| Name                                                | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                            |
| --------------------------------------------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| account\_name<mark style="color:red;">\*</mark>     | String | The name of the beneficiary. Must exactly match the name of the account holder to ensure payment delivery.                                                                                                                                                                                                                                                                                                             |
| account\_number                                     | String | The account number of the bank account. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                                                                                                                                                                                      |
| currency<mark style="color:red;">\*</mark>          | String | The currency that the bank account accepts. E.g. 'usd', 'eur'.                                                                                                                                                                                                                                                                                                                                                         |
| address\_line1<mark style="color:red;">\*</mark>    | String | The first line of the address of the person or organisation that controls the bank account.                                                                                                                                                                                                                                                                                                                            |
| address\_line2                                      | String | The second line of the address of the person or organisation that controls the bank account.                                                                                                                                                                                                                                                                                                                           |
| city<mark style="color:red;">\*</mark>              | String | The city where the person or organisation that controls the bank account is located.                                                                                                                                                                                                                                                                                                                                   |
| state                                               | String | The state/district where the person or organisation that controls the bank account is located. Required if country is `US`                                                                                                                                                                                                                                                                                             |
| postal\_code<mark style="color:red;">\*</mark>      | String | The postal/zip code where the person or organisation that controls the bank account is located.                                                                                                                                                                                                                                                                                                                        |
| country<mark style="color:red;">\*</mark>           | String | The country where the person or organisation that controls the bank account is located. Given in ISO 3166-1 alpha-2 format.                                                                                                                                                                                                                                                                                            |
| beneficiary\_type<mark style="color:red;">\*</mark> | String | `individual` or `business`                                                                                                                                                                                                                                                                                                                                                                                             |
| routing\_number                                     | String | The ACH routing number of the bank account. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                                                                                                                                                                                  |
| bank\_name<mark style="color:red;">\*</mark>        | String | The name of the bank associated with the account. e.g. 'Revolut'                                                                                                                                                                                                                                                                                                                                                       |
| sort\_code                                          | String | The sort code of the bank account. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                                                                                                                                                                                           |
| iban                                                | String | The IBAN of the bank account. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                                                                                                                                                                                                |
| swift\_bic                                          | String | The swift/bic of the bank account. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                                                                                                                                                                                           |
| document\_number                                    | String | The recipient's CUIT (tax number). See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                                                                                                                                                                                           |
| account\_type                                       | String | `checking` or `savings`. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                                                                                                                                                                                                     |
| rib\_number                                         | String | The recipient's Relevé d'Identité Bancaire number. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                                                                                                                                                                           |
| bsb\_number                                         | String | The recipient's BSB number. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                                                                                                                                                                                                  |
| rails                                               | String | <p>If the account is on the SWIFT network, put the value of this attribute to<code>swift</code>. Otherwise if it is SEPA/ACH or other local rails you can set it to <code>local</code>. If you leave this attribute blank it will default to <code>local</code>. There is also a <code>wire</code> option.<br><br>Please see <a href="rail-availability.md">Rail Availability</a> to understand what is supported.</p> |
| ncc                                                 | String | The ncc of the bank account. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                                                                                                                                                                                                 |
| branch\_code                                        | String | The branch\_code of the bank account. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                                                                                                                                                                                        |
| bank\_code                                          | String | The bank\_code of the account. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                                                                                                                                                                                               |
| date\_of\_birth<mark style="color:red;">\*</mark>   | String | The date of birth of the recipient. Required for `individuals`                                                                                                                                                                                                                                                                                                                                                         |
| ifsc                                                | String | The ifsc of the bank account. See [here](required-fields-for-currencies.md) what currencies require it.                                                                                                                                                                                                                                                                                                                |

{% tabs %}
{% tab title="200: OK " %}
```json
{
    "payment_detail": {
        "id": "fa898aec-519c-46be-9b4c-e76ef4ff99d9",
        "user_id": "a25a4274-8f50-4579-b476-8f35b297d4ad",
        "bank_name": "Chase",
        "account_name": "ACME Ltd",
        "iban": null",
        "swift_bic": null,
        "ifsc": null,
        "rib_number": null,
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
        "date_of_birth": "12/12/1985",
        "country": "US",
        "status": "approved",
        "rails": "local"
    }
}
```
{% endtab %}
{% endtabs %}
