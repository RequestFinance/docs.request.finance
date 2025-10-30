---
description: Fetch all fiat payouts associated with a user
---

# Offramps#Index

#### Example Request

```json
curl https://{{base_url}}/users/USER_ID/offramps \
-X GET \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json" \
```

#### Endpoint Information

## Index Offramps

<mark style="color:blue;">`GET`</mark> `https://{{base_url}}/users/:user_id/offramps`

#### Path Parameters

| Name                                       | Type | Description                                           |
| ------------------------------------------ | ---- | ----------------------------------------------------- |
| user\_id<mark style="color:red;">\*</mark> | UUID | The ID for the user whose offramps you want to fetch. |

{% tabs %}
{% tab title="200: OK " %}
<pre class="language-javascript"><code class="lang-javascript">{ 
   "offramps": [
<strong>      {
</strong>         id: "074cb3e4-1f56-4916-8024-ecbf6f805b90",
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
         supporting_document: {
            submitted_url: "https://web3accounting.com/invoices/in_378949x.pdf",
            status: "not_checked"
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
         supporting_document: {
            submitted_url: null,
            status: null
         }
      }
   ]
}
</code></pre>
{% endtab %}
{% endtabs %}
