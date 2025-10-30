---
description: >-
  Create a Quote that will tell you how much you need to send and to what
  address.
---

# Quotes#Create

Please read [How To Make a Payment](how-to-make-a-payment.md) to understand how Quotes & Offramps work.

**Example request**

```json
curl https://{{base_url}}/users/USER_ID/quotes
-X POST \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json" \
-d '{
       "quote": {
          "deposit_token": "usdc",
          "deposit_token_chain": "ethereum"
       }
}'
```

**Endpoint Information**

## Create a quote

<mark style="color:green;">`POST`</mark> `https://{{base_url}}/users/:user_id/quotes`

Get the required information to create an offramp.

#### Path Parameters

| Name                                       | Type | Description                                    |
| ------------------------------------------ | ---- | ---------------------------------------------- |
| user\_id<mark style="color:red;">\*</mark> | UUID | The ID for the User who is making the payment. |

#### Request Body

| Name                                                    | Type   | Description                                                                                           |
| ------------------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------------- |
| deposit\_token<mark style="color:red;">\*</mark>        | String | Symbol of the token to be liquidated. Can only be `usdc`.                                             |
| deposit\_token\_chain<mark style="color:red;">\*</mark> | String | Blockchain of the token to be liquidated. Can be `polygon`, `ethereum`, `tron`, `solana`, `arbitrum`. |

{% tabs %}
{% tab title="200: OK " %}
<pre class="language-json"><code class="lang-json"><strong>{ 
</strong>  "quote":
    {
      "id": "1e99d470-dcc2-46f4-970c-bc35a9e13b84",
      "user_id": "a25a4274-8f50-4579-b476-8f35b297d4ad"
      "deposit_token": "usdc",
      "deposit_token_chain": "ethereum",
      "deposit_token_amount": 0,
      "fees": 0,
      "expiry": 1366762500
      "executed": false,
      "rates": {}
    },
    "deposit_address": {
      "adddress": "0x709c56AfDAdBDCAB4f7a6aAe99644C91C3eF67eF",
      "blockchain": "ethereum"
    },
    "offramps": []
}
</code></pre>


{% endtab %}
{% endtabs %}
