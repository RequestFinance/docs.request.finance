---
description: Submits the Quote to begin processing to fiat.
---

# Quotes#Execute

**Example request**

```json
curl https://{{base_url}}/users/USER_ID/quotes/QUOTE_ID/execute
-X POST \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json" \
-d '{
      "quote": {
         "crypto_transfer": {
            "tx_id": "0x65be7196da49cd3f5c3f6a0ff0f1583910a6b6c9a8a28946adfa1084dd76d657",
            "blockchain": "polygon",
            "network": "mainnet"
          }
      }
    }
}'
```

**Endpoint Information**

## Execute a Quote

<mark style="color:green;">`POST`</mark> `https://{{base_url}}/users/:user_id/quotes/:quote_id/execute`

Send a Quote for processing

#### Path Parameters

| Name                                        | Type | Description                                    |
| ------------------------------------------- | ---- | ---------------------------------------------- |
| user\_id<mark style="color:red;">\*</mark>  | UUID | The ID for the User who is making the payment. |
| quote\_id<mark style="color:red;">\*</mark> | UUID | The ID of the Quote that has been fulfilled.   |

#### Request Body

| Name                                         | Type   | Description                                                                                                             |
| -------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------- |
| tx\_id<mark style="color:red;">\*</mark>     | String | The transaction hash of the crypto transfer that was made to the deposit address.                                       |
| blockchain<mark style="color:red;">\*</mark> | String | The blockchain the crypto transfer to the deposit address was made on (e.g. 'ethereum', 'polygon', 'tron', 'arbitrum'). |
| network<mark style="color:red;">\*</mark>    | String | The network the crypto transfer to the deposit address was made on (e.g. 'mainnet', 'sepolia').                         |

{% tabs %}
{% tab title="200: OK " %}
<pre class="language-json"><code class="lang-json"><strong>{ 
</strong>  "quote":
    {
      "id": "1e99d470-dcc2-46f4-970c-bc35a9e13b84",
      "deposit_token": "usdc",
      "deposit_token_chain": "ethereum",
      "deposit_token_amount": 21718,
      "expiry": 1366762500,
      "fees": 10.0,
      "rates": {
          "eur": 0.92118,
       },
      "executed": true
    },
    "deposit_address": {
      "adddress": "0x709c56AfDAdBDCAB4f7a6aAe99644C91C3eF67eF",
      "blockchain": "ethereum"
    },
    "crypto_transfer": {
      "tx_id": "0x65be7196da49cd3f5c3f6a0ff0f1583910a6b6c9a8a28946adfa1084dd76d657",
      "blockchain": "ethereum",
      "network": "mainnet"
    },
    "offramps": [
      {
         "id": "074cb3e4-1f56-4916-8024-ecbf6f805b90",
         "user_id": "a25a4274-8f50-4579-b476-8f35b297d4ad",
         "payment_detail_id": "fa898aec-519c-46be-9b4c-e76ef4ff99d9",
         "quote_id": "1e99d470-dcc2-46f4-970c-bc35a9e13b84",
         "status": "initiated",
         "status_message": null,
         "destination_amount": 19000,
         "destination_currency": "eur",
         "rails": "local",
         "reference": "Payment for Services #1010",
         "supporting_document": {
            "submitted_url": "https://web3accounting.com/invoices/in_378949x.pdf",
            "status": "not_checked"
         }
      },
      {
         "id": "074cb3e4-1f56-4916-8024-ecbf6f805b90",
         "user_id": "a25a4274-8f50-4579-b476-8f35b297d4ad",
         "payment_detail_id": "576b17c9-db11-4593-a362-52605408a1b5",
         "quote_id": "1e99d470-dcc2-46f4-970c-bc35a9e13b84",
         "status": "initiated",
         "status_message": null,
         "destination_amount": 1000,
         "destination_currency": "eur",
         "rails": "local",
         "reference": "Payment for Services #1011",
         "supporting_document": null
      }
   ]
}
</code></pre>


{% endtab %}
{% endtabs %}
