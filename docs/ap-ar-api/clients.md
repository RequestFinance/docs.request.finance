# Clients

{% hint style="warning" %}
Contrary to invoices, there is no test environment for clients. Editing client information with a test API key WILL change the client on production.
{% endhint %}

## Creating a Client

<mark style="color:green;">`POST`</mark> `https://api.request.finance/clients`

#### Request Body

<table><thead><tr><th>Name</th><th width="135">Type</th><th>Description</th></tr></thead><tbody><tr><td>email (*)</td><td>String</td><td></td></tr><tr><td>contactType (*)</td><td>String[]</td><td>Should be ["customer"] (mind the array!)</td></tr><tr><td>jobTitle</td><td>String</td><td></td></tr><tr><td>department</td><td>String</td><td></td></tr><tr><td>paymentMethods</td><td></td><td></td></tr><tr><td>address.streetAddress</td><td>String</td><td></td></tr><tr><td>address.extendedAddress</td><td>String</td><td></td></tr><tr><td>address.city</td><td>String</td><td></td></tr><tr><td>address.postalCode</td><td>String</td><td></td></tr><tr><td>address.region</td><td>String</td><td>(e.g. “California”)</td></tr><tr><td>address.country</td><td>String</td><td>Two character ISO 3166-1 country code of the buyer.</td></tr><tr><td>businessName</td><td>String</td><td></td></tr><tr><td>firstName</td><td>String</td><td></td></tr><tr><td>lastName</td><td>String</td><td></td></tr><tr><td>phone</td><td>String</td><td></td></tr><tr><td>taxRegistration</td><td>String</td><td>Tax number</td></tr></tbody></table>

Mandatory fields are marked with (\*).

{% tabs %}
{% tab title="201" %}
```
{
    "id": "[clientId]",
    // ... Client details
    "createdById": "...", // User's ID
    "createdDate": "2024-05-17T16:21:24.658Z"
}
```
{% endtab %}
{% endtabs %}

Note that you don't have to have your clients created to issue invoices programmatically.

## Updating a Client

<mark style="color:green;">`PUT`</mark> `https://api.request.finance/clients/[clientId]`

#### Request Body

Same as for the creation: [#request-body](clients.md#request-body "mention")

## Retrieving clients

You can list all clients with:

<mark style="color:green;">`GET`</mark>`https://api.request.finance/clients?type=customer`

{% hint style="info" %}
`Note that the list of clients is not paginated. If you wish to manage a big number of clients, you probably want to consider issuing some invoices through API, see` [invoices.md](invoices.md "mention"). Reach out to us via the Intercom widget for specific needs.
{% endhint %}

Get the details of one client with:

<mark style="color:green;">`GET`</mark>`https://api.request.finance/clients/[clientId]`
