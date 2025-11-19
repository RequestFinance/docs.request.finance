---
description: Tell us which banks we should pay once your Quote is executed.
---

# Offramps#Create

Please read [How To Make a Payment](../quotes/how-to-make-a-payment.md) to understand how Quotes & Offramps work.

#### Example Request

```json
curl https://{{base_url}}/users/USER_ID/quotes/QUOTE_ID/offramps \
-X POST \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json" \
-d '{
    "offramps": [
        {
            "payment_detail_id": "fa898aec-519c-46be-9b4c-e76ef4ff99d9",
            "destination_amount": 19000,
            "destination_currency": "usd",
            "rails": "swift",
            "reference": "Payment for Services #1010",
            "metadata": {
                "custom_key": "custom_value"
            }
        },
        {
            "payment_detail_id": "576b17c9-db11-4593-a362-52605408a1b5",
            "destination_amount": 1000,
            "destination_currency": "eur",
            "rails": "swift",
            "reference": "Payment for Services #1011"
        }
    ]
}' 
```

#### Endpoint Information

## Create Offramps

<mark style="color:green;">`POST`</mark> `https://{{base_url}}/users/:user_id/quotes/:quote_id/offramps`

#### Path Parameters

| Name                                        | Type | Description                                          |
| ------------------------------------------- | ---- | ---------------------------------------------------- |
| user\_id<mark style="color:red;">\*</mark>  | UUID | The ID for the user who is making the payment.       |
| quote\_id<mark style="color:red;">\*</mark> | UUID | The ID for the Quote which these payments relate to. |

#### Request Body

| Name                                                    | Type   | Description                                                                                                                                                             |
| ------------------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| payment\_detail\_id<mark style="color:red;">\*</mark>   | UUID   | The ID of the Payment Detail (bank account) where the fiat payment should be made to.                                                                                   |
| destination\_amount<mark style="color:red;">\*</mark>   | String | The amount in fiat currency that should be delivered to the Payment Detail. The amount must be over the minimum limit of the `destination_currency`.                    |
| reference                                               | String | The reference message you would like on the fiat payment.                                                                                                               |
| destination\_currency<mark style="color:red;">\*</mark> | String | The currency that should be delivered to the Payment Detail, e.g. `usd, eur`                                                                                            |
| rails                                                   | String | Choose between `local,` `swift,`and `wire.` Defaults to `local`. Check what [options](../payment-details/rail-availability.md) are available for your desired currency. |
| metadata                                                | Object | An object which can contain a custom key/value pair.                                                                                                                    |

{% tabs %}
{% tab title="200: OK " %}
```javascript
{ 
   "offramps": [
      {
         id: "074cb3e4-1f56-4916-8024-ecbf6f805b90",
         user_id: "a25a4274-8f50-4579-b476-8f35b297d4ad",
         payment_detail_id: "fa898aec-519c-46be-9b4c-e76ef4ff99d9",
         quote_id: "1e99d470-dcc2-46f4-970c-bc35a9e13b84",
         status: "initiated",
         status_message: null,
         destination_amount: 19000,
         destination_currency: "usd",
         reference: "Payment for Services #1010",
         rails: "swift",
         rate: 0.92820,
         fee: 125,
         "metadata": {
             "custom_key": "custom_value"
         }
      },
      {
         id: "074cb3e4-1f56-4916-8024-ecbf6f805b90",
         user_id: "a25a4274-8f50-4579-b476-8f35b297d4ad",
         payment_detail_id: "576b17c9-db11-4593-a362-52605408a1b5",
         quote_id: "1e99d470-dcc2-46f4-970c-bc35a9e13b84",
         status: "initiated",
         status_message: null,
         destination_amount: 1000,
         destination_currency: "eur",
         reference: "Payment for Services #1011",
         rails: "local",
         rate: 0.85660,
         fee: 4,
         "metadata": {}
      }
   ]
}
```
{% endtab %}
{% endtabs %}

**Minimum Limits**

Please see the [Minimum Limits](limitations.md) section to ensure your Offramp meets the minimum amounts.
