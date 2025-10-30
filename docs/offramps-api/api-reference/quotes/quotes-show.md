---
description: Check how much it will cost to settle your payment(s).
---

# Quotes#Show

**Example request**

```json
curl https://{{base_url}}/users/USER_ID/quotes/QUOTE_ID
-X GET \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json"
```

**Endpoint information**

## Show a Quote

<mark style="color:blue;">`GET`</mark> `https://{{base_url}}/users/:user_id/quotes/:quote_id`

See the total amount required to pay to deliver the requested Offramps

#### Path Parameters

| Name                                        | Type | Description                                         |
| ------------------------------------------- | ---- | --------------------------------------------------- |
| quote\_id<mark style="color:red;">\*</mark> | UUID | The ID for the quote you wish to retrieve           |
| user\_id<mark style="color:red;">\*</mark>  | UUID | The ID for the user who the quote is being made for |

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
    "crypto_transfer": null,
    "offramps": []
}
</code></pre>
{% endtab %}
{% endtabs %}
