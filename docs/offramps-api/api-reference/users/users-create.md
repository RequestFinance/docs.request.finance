# Users#Create

## Creating a user

#### Example Request

```json
curl https://{{base_url}}/users
-X POST \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json" \
-d '{
    "user": {
        "beneficiary_type": "individual",
        "first_name": "Marco",
        "last_name": "Pierre White",
        "company_name": null,
        "email": "marco@cheq.xyz",
        "date_of_birth": "12/12/1985",
        "address_line1": "2 Bellevue Road",
        "address_line2": "Wandsworth Common",
        "city": "London",
        "state": "London",
        "postcode": "SW177EG",
        "country": "GB",
        "nationality": "GB",
        "phone": "+447515772386",
        "ssn": null,
        "source_of_funds": null,
        "business_activity": null
    }
}'
```

#### Endpoint Information

## Create User

<mark style="color:green;">`POST`</mark> `https://{{base_url}}/users`

Create a new Pay.so user

#### Request Body

| Name                                                | Type   | Description                                                                                                                                                                                                                                                                                                                                                                   |
| --------------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| first\_name                                         | String | The user's legally recognised first name, as shown on their identity document. Required if `beneficiary_type` is `individual`.                                                                                                                                                                                                                                                |
| address\_line1<mark style="color:red;">\*</mark>    | String | The first line of the address where the `individual` resides or the `business`'s registered office address.                                                                                                                                                                                                                                                                   |
| address\_line2                                      | String | The second line of the address where the `individual` resides or the `business`'s registered office address.                                                                                                                                                                                                                                                                  |
| city<mark style="color:red;">\*</mark>              | String | The city where the `individual` resides or the `business`'s registered office is based.                                                                                                                                                                                                                                                                                       |
| last\_name                                          | String | The user's legally recognised last name, as shown on their identity document. Required if `beneficiary_type` is `individual`.                                                                                                                                                                                                                                                 |
| country<mark style="color:red;">\*</mark>           | String | The country where the `individual` resides or the `business`'s registered office is based, in ISO 3166-1 alpha-2 format (e.g. 'GB' for the United Kingdom).                                                                                                                                                                                                                   |
| date\_of\_birth<mark style="color:red;">\*</mark>   | Date   | The `individual`'s date of birth or `business`'s date of incorporation.                                                                                                                                                                                                                                                                                                       |
| email<mark style="color:red;">\*</mark>             | String | The contact email for the user.                                                                                                                                                                                                                                                                                                                                               |
| postcode<mark style="color:red;">\*</mark>          | String | The postal/zip code where the `individual` resides or the `business`'s registered office is based.                                                                                                                                                                                                                                                                            |
| state<mark style="color:red;">\*</mark>             | String | The state/county/district where the `individual` resides or the `business`'s registered office is based. If the entity is based in the US, the state must be formatted to two letters e.g. 'CA' for California                                                                                                                                                                |
| ssn<mark style="color:red;">\*</mark>               | String | <p>If you are adding a US <code>individual</code>. Use SSN number.<br><br>If this is a US <code>business</code>, use an EIN number. <br><br>If it is an international <code>business</code>, use a registration number. <br><br>If you are adding an <code>individual</code> based outside of the US, use a number similar to a Social Security Number for their country.</p> |
| beneficiary\_type<mark style="color:red;">\*</mark> | String | Specify whether the user is an `individual` or a `business`                                                                                                                                                                                                                                                                                                                   |
| company\_name                                       | String | The company's legal name. Required if `beneficiary_type` is `business`.                                                                                                                                                                                                                                                                                                       |
| phone<mark style="color:red;">\*</mark>             | String | The phone number of the `individual` or `business.`                                                                                                                                                                                                                                                                                                                           |
| source\_of\_funds                                   | String | A short description of how the business is funded. For example: 'Venture Capital' or 'Token Sale'. Only required if user is a `business`                                                                                                                                                                                                                                      |
| business\_activity                                  | String | A short statement about the business's activity. E.g. 'An API service facilitating crypto-to-fiat payments to third parties'.                                                                                                                                                                                                                                                 |
| nationality<mark style="color:red;">\*</mark>       | String | The country where the `individual` was born in ISO 3166-1 alpha-2 format (e.g. 'GB' for the United Kingdom).                                                                                                                                                                                                                                                                  |

{% tabs %}
{% tab title="200: OK " %}
```json
{
    "user": {
        "id": "a25a4274-8f50-4579-b476-8f35b297d4ad",
        "beneficiary_type": "individual",
        "first_name": "Marco",
        "last_name": "Pierre White",
        "company_name": null,
        "email": "marco@cheq.xyz",
        "date_of_birth": "12/12/1985",
        "address_line1": "2 Bellevue Road",
        "address_line2": "Wandsworth Common",
        "city": "London",
        "state": "London",
        "postcode": "SW177EG",
        "country": "GB",
        "ssn": null,
        "website": null,
        "source_of_funds": null,
        "business_description": null,
        "kyc": {
            "general": {
                "status": "not_started",
                "moderation_comment": null
            },
            "eur": {
                "status": "not_started",
                "swift_status": "not_started"
            },
            "usd": {
                "status": "not_started",
                "swift_status": "not_started"
            },
            "ars": {
                "status": "not_started",
                "swift_status": "not_started"
            }
        }
    }
}
```
{% endtab %}
{% endtabs %}



{% hint style="info" %}
Users cannot be created from the following countries:\
`[AF BY BA BI CF CU KP CD ET GT GN GW HT IR IQ LB LY ML MM NI NE RU SO SS SD SY TN VE YE ZW]`
{% endhint %}

