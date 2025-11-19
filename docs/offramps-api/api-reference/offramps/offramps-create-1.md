---
description: >-
  This endpoint enables you to provide a document associated with your
  off-ramps. This upload is mandatory for us to process your off-ramps. You can
  upload your document before or after executing quotes
---

# Upload Offramp Supporting Document

#### Example Request

```json
curl https://{{base_url}}/offramps/:offrampId/supporting-documents \
-X POST \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: multipart/form-data"
```

#### Endpoint Information

## Upload Offramp Supporting Document

<mark style="color:green;">`POST`</mark> `https://{{base_url}}/offramps/:offramp_id/supporting-documents`

#### Path Parameters

| Name                                          | Type | Description           |
| --------------------------------------------- | ---- | --------------------- |
| offramp\_id<mark style="color:red;">\*</mark> | UUID | The ID of the offramp |

#### Request Body

| Name                                   | Type | Description                                        |
| -------------------------------------- | ---- | -------------------------------------------------- |
| file<mark style="color:red;">\*</mark> | File | PDF, JPG, or PNG file with maximum of 5 MB in size |

{% tabs %}
{% tab title="200: OK " %}
```javascript
{ 
   "message": "Document uploaded successfully"
}
```
{% endtab %}
{% endtabs %}

**Limitation**

We only support 1 document per offramp. If you call this endpoint multiple times, the latest document will overwrite any previous ones.
