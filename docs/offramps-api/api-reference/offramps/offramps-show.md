---
description: See the progress of a particular fiat payout.
---

# Offramps#Show

**Example request**

```json
curl https://{{base_url}}/users/USER_ID/offramps/OFFRAMP_ID
-X GET \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json"
```

#### **Example Response**

## Get an Offramp

<mark style="color:blue;">`GET`</mark> `https://{{base_url}}/users/:user_id/offramps/:offramp_id`

#### Path Parameters

| Name                                          | Type | Description                                    |
| --------------------------------------------- | ---- | ---------------------------------------------- |
| user\_id<mark style="color:red;">\*</mark>    | UUID | The ID of the User associated with the Offramp |
| offramp\_id<mark style="color:red;">\*</mark> | UUID | The ID of the Offramp you wish to retrieve     |

{% tabs %}
{% tab title="200: OK " %}
```json
{
   "offramp": {
       "id": "074cb3e4-1f56-4916-8024-ecbf6f805b90",
       "user_id": "a25a4274-8f50-4579-b476-8f35b297d4ad",
       "quote_id": "1e99d470-dcc2-46f4-970c-bc35a9e13b84",
       "payment_detail_id": "fa898aec-519c-46be-9b4c-e76ef4ff99d9",
       "status": "initiated",
       "status_message": null,
       "destination_amount": 19000,
       "destination_currency": "usd",
       "reference": "Payment for Services #1010",
       "rails": "swift",
       "rate": 0.92820,
       "fee": 125,
       "supporting_document": {
           "submitted_url": "https://web3accounting.com/invoices/in_378949x.pdf",
           "status": "not_checked"
       }
   }
}
```
{% endtab %}
{% endtabs %}

