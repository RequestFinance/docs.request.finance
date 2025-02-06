# Organizations

Users can share their personal account data by inviting team members and assigning them particular roles (Admin, Finance Manager, Accountant, and Approver). Each role comes with specific permissions, which you can find [in our FAQ](https://help.request.finance/en/articles/8622864-what-roles-are-available).

The user holding the account's data is called the **organization owner** and has the same set of permissions as any other admin. The owner of an organization cannot change by design.

To summarize, each user owns a personal account. As soon as they share it with other users by inviting them, it essentially creates an **Organization**.

## Listing Organizations

The following endpoint retrieves the list of organizations a user belongs to. This list does not include the user's account (personal account) but only external organizations that they have been invited to.

{% hint style="warning" %}
**Important**: This endpoint is only available with the OAuth authentication scheme, not API keys. You need to ask for the `user:read` OAuth scope when retrieving a token in order to have access to this endpoint.
{% endhint %}

## List organizations the user belongs to

<mark style="color:blue;">`GET`</mark> `https://api.request.finance/users/organizations`

{% tabs %}
{% tab title="200: OK " %}
```json
[
  {
    "id": "654b9aaefb9eb1ddde2cf85f",
    "name": "acme-org",
    "displayName": "Acme Org",
    "role": "admin",
    "owner": {
      "id": "654b9aaa00137146c4fd7e54",
      "email": "bills@acme.com",
      "firstname": "Bills",
      "lastname": "AcmeOrg"
    }
  }
]
```
{% endtab %}
{% endtabs %}

## Accessing an Organization's Data

When querying Request Finance's API with a user's OAuth token, you will retrieve the user's personal account data.

To access data from an Organization this user belongs to, add the following header to each API call:

```http
X-Organization: [ID]
```

Use the [#listing-organizations](organizations.md#listing-organizations "mention") API endpoint to retrieve the proper organization ID. For instance:

```http
X-Organization: 654b9aaefb9eb1ddde2cf85f
```

{% hint style="info" %}
If the user is the owner of the organization, you don't need to add the `X-Organization` header. Their personal account itself constitutes the organization; accessing the user's data is like accessing the organization's data.
{% endhint %}

When fetching user's data with the `GET /users` endpoint, the `organization` field corresponds to the organization the user is currently logged in with:

* It is always equal to `X-Organization` when the header is set.
* If the `X-Organization` header is not set, but the user is an owner, then the owned organization is returned.
* If the `X-Organization` header is not set, and the user does not own an organization, the field is set to `null`.
