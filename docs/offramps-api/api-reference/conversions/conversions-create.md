# Conversions#Create

## Instantiate a Conversion Object

#### Conversion Example Request

```json
curl https://{{v1_base_url}}/conversions
-X POST \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json" \
-d '{
    "conversion": {
        "input_currency": "usdc",
        "input_amount": 1000,
        "output_currency": "eur",
        "output_amount": null,
        "mode": "sending",
    }
}'
```

#### Endpoint Information

## Create Conversion

<mark style="color:green;">`POST`</mark> `https://{{v1_base_url}}/conversions`

#### Request Body

| Name             | Type   | Description                                                                                                                                                                                                                                                                            |
| ---------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| input\_currency  | String | <p>The currency the sender will send. <br><br>For offramps the available input currencies are <code>usdt</code> or <code>usdc</code>.</p>                                                                                                                                              |
| output\_currency | String | <p>The currency the recipient will receive. <br><br>For offramps the available currencies can be found <a href="https://app.gitbook.com/o/w4HdDXsE3BZOtl062S9D/s/Y9rr7VZATzF9cXJogqcZ/api-reference/payment-details/required-fields-for-currencies">here</a>. </p>                     |
| input\_amount    | Float  | The sending amount                                                                                                                                                                                                                                                                     |
| output\_amount   | Float  | The receiving amount                                                                                                                                                                                                                                                                   |
| mode             | String | <p>The two available modes are <code>sending</code> and <code>receiving</code>.<br><br>When the mode is sending the input amount will be used to calculate the received amount.<br><br>When the mode is receiving, the output amount will be used to calculate the sending amount.</p> |

{% tabs %}
{% tab title="200: OK " %}
```json
{
    "conversion": {
        "exchange_rate": { 'usd_eur' => 0.914386 },
        "fees": 8.687,
        "input_currency": "usdc",
        "output_currency": "eur",
        "input_amount": 1000.0,
        "output_amount": 906,
        "mode": "sending"
        }
}
```
{% endtab %}
{% endtabs %}

