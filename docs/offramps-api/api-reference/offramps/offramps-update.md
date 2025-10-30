---
description: Update an Offramp's reference
---

# Offramps#Update

{% hint style="warning" %}
Please note the following information.

* The only attribute that can be updated is the reference.
* USD local offramps cannot be modified.
* Offramps cannot be updated once they have moved beyond the “initiated” status.
{% endhint %}

#### Example Request

```json
curl https://{{base_url}}/users/USER_ID/quotes/QUOTE_ID/offramps/OFFRAMP_ID \
-X PATCH \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json" \
-d '{
    "offramp": {
        "reference": "new_reference"
    }
}' 
```

#### Endpoint Information

## Create Offramps

<mark style="color:green;">`PATCH`</mark> `https://{{base_url}}/users/:user_id/quotes/:quote_id/offramps/:offramp_id`

#### Path Parameters

| Name                                          | Type | Description                                            |
| --------------------------------------------- | ---- | ------------------------------------------------------ |
| user\_id<mark style="color:red;">\*</mark>    | UUID | The ID for the user who is making the payment.         |
| quote\_id<mark style="color:red;">\*</mark>   | UUID | The ID for the Quote which these payments relate to.   |
| offramp\_id<mark style="color:red;">\*</mark> | UUID | The ID for the Offramp which these payments relate to. |

#### Request Body

| Name      | Type   | Description                                                                          |
| --------- | ------ | ------------------------------------------------------------------------------------ |
| reference | String | The reference message you would like on the fiat payment (only works on EUR routes). |

{% tabs %}
{% tab title="200: OK " %}
```javascript
{ 
   "offramp": {
         id: "074cb3e4-1f56-4916-8024-ecbf6f805b90",
         user_id: "a25a4274-8f50-4579-b476-8f35b297d4ad",
         payment_detail_id: "fa898aec-519c-46be-9b4c-e76ef4ff99d9",
         quote_id: "1e99d470-dcc2-46f4-970c-bc35a9e13b84",
         status: "initiated",
         status_message: null,
         destination_amount: 19000,
         destination_currency: "usd",
         reference: "new_reference",
         rails: "swift",
         rate: 0.92820,
         fee: 125,
         supporting_document: {
            submitted_url: "https://web3accounting.com/invoices/in_378949x.pdf",
            status: "not_checked"
         },
         "metadata": {
             "custom_key": "custom_value"
         }
      }
}
```
{% endtab %}
{% endtabs %}
