# Authentication

### API Key

We'll supply you with API key to help you get going with our API.

The API key must be passed into each request via the `Authorization` header. (Replacing YOUR\_API\_KEY as per the example below).

#### Example Request

```json
curl https://{{base_url}}/ENDPOINT
-X GET \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json" \
```
