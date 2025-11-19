# Retrieving Unhosted Wallet Verification Link

Upon receiving the [Travel Rule webhook](https://docs.request.finance/on-offramps-api/api-reference/webhooks/payment-detail-webhook-1), use the `quote_id` to retrieve the verification link

#### Example Request

```json
curl https://{{base_url}}/users/:userId/travel-rules
-X POST \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json" \
-d '{
    "quote_id": "e8d2ce3f-0c44-4cb4-8474-1ac8af91842a"
}'
```

#### Endpoint Information

<mark style="color:green;">`POST`</mark> `https://{{base_url}}/users/:user_id/travel-rules`

#### Path Parameters

| Name                                       | Type | Description    |
| ------------------------------------------ | ---- | -------------- |
| user\_id<mark style="color:red;">\*</mark> | UUID | ID of the User |

#### Request Body

| Name                                        | Type   | Description                                           |
| ------------------------------------------- | ------ | ----------------------------------------------------- |
| quote\_id<mark style="color:red;">\*</mark> | String | The `quote_id` retrieved from the Travel Rule webhook |

{% tabs %}
{% tab title="200: OK " %}
```json
{
    "url": "https://sumsub.com/websdk/p/7JwtC0pb9mcqQsLb"
}
```
{% endtab %}
{% endtabs %}
