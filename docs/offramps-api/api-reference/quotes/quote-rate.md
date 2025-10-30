# Quote#Rate

In some cases you may want to allow your users to provide either the amount they want the recipient to receive or the amount of crypto the sender wishes to send. In such a case our API will calculate the other half and provide a breakdown of the exchange rate and associated fees.

{% hint style="danger" %}
This feature only supports payouts to one recipient. Batch payout functionality is not supported with this feature.
{% endhint %}

**Example request**

```json
curl https://{{base_url}}/users/USER_ID/quote/rate
-X POST \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json" \
-d '{
       "quote": {
          "deposit_token_amount": 1000,
          "rails": "wire",
          "fiat_currency": "usd",
          "deposit_token": "usdc",
          "deposit_token_chain": "ethereum",
          "fiat_amount": nil,
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

| Name                                                    | Type   | Description                                                                                                  |
| ------------------------------------------------------- | ------ | ------------------------------------------------------------------------------------------------------------ |
| deposit\_token<mark style="color:red;">\*</mark>        | String | Symbol of the token to be liquidated. Can be  only be `usdc`.                                                |
| deposit\_token\_chain<mark style="color:red;">\*</mark> | String | Blockchain of the token to be liquidated. Can be `polygon`, `ethereum`, `solana`,`tron`.                     |
| deposit\_token\_amount                                  | String | How much crypto the user would like to send. Must be supplied if `fiat_amount`  is nil                       |
| rails                                                   | String | The fiat payout rail you would like to use. Values can be `nil`, `local`, `swift`, `wire` (for usd payments) |
| fiat\_currency<mark style="color:red;">\*</mark>        | String | The fiat payout currency                                                                                     |
| fiat\_amount                                            | String | How much fiat the recipient should receive. Must be supplied if `deposit_token_amount`  is nil               |

{% tabs %}
{% tab title="200: OK " %}
<pre class="language-json"><code class="lang-json"><strong>{ 
</strong>  "quote":
    {
      "id": "2a013048-614c-4bbb-a157-958d401141fc",
      "deposit_token": "usdc",
      "deposit_token_chain": "ethereum",
      "deposit_token_amount": 1023,
      "fiat_amount": 1000,
      "fiat_currency": "usd",
      "currency_pair": "usdcusd"
      "fees": 3,
      "rails": "wire",
      "expiry": 1366762500
      "executed": false,
      "rate": '0.99999'
    },
    "deposit_address": {
      "adddress": "0x709c56AfDAdBDCAB4f7a6aAe99644C91C3eF67eF",
      "blockchain": "ethereum"
    },
}
</code></pre>


{% endtab %}
{% endtabs %}
