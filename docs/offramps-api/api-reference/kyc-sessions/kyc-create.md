# KYC#Create

## Creating a KYC Session

#### Example Request

```json
curl https://{{base_url}}/users/USER_ID/kycs
-X POST \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json"
```

#### Endpoint Information

## &#x20;Create KYC session

<mark style="color:green;">`POST`</mark> `https://{{base_url}}/users/:user_id/kycs`

Create a KYC session for a user.

#### Path Parameters

| Name                                       | Type | Description                                            |
| ------------------------------------------ | ---- | ------------------------------------------------------ |
| user\_id<mark style="color:red;">\*</mark> | UUID | The ID of the user in for whom you want a KYC session. |

{% tabs %}
{% tab title="200: OK " %}
```javascript
{
   kyc: {
      user_id: "a25a4274-8f50-4579-b476-8f35b297d4ad",
      url: "https://sumsub.com/idensic/l/#/sbx_VvK9E9P2A23xQPoA"
   }
}
```
{% endtab %}
{% endtabs %}

