# Field Requirements For Local Currency Payouts

The following currencies are available for Local payouts. Please note our [Required Fields For All Currencies Section](field-requirements-for-local-currency-payouts.md#required-fields-for-all-currencies)

* [Required Fields For All Currencies](field-requirements-for-local-currency-payouts.md#required-fields-for-all-currencies)
* [Euro (EUR)](field-requirements-for-local-currency-payouts.md#additional-eur-local-fields)
* [Great British Pound (GBP)](field-requirements-for-local-currency-payouts.md#additional-gbp-local-fields)
* [United States Dollar (USD)](field-requirements-for-local-currency-payouts.md#additional-usd-local-fields)

### Required Fields For All Currencies

{% hint style="info" %}
Please ensure that you supply the following bank account information for **every** payment\_detail you create.
{% endhint %}

* address\_line1
* city
* postal\_code
* country
* account\_name
* currency
* beneficiary\_type
* bank\_name

### EUR Local Field Validations

| Field             | Regex                                                                                                              |
| ----------------- | ------------------------------------------------------------------------------------------------------------------ |
| address\_line1    | -                                                                                                                  |
| city              | -                                                                                                                  |
| postal\_code      | -                                                                                                                  |
| country           | ISO 3166-1 alpha-2 format                                                                                          |
| account\_name     | /^\[A-Za-z0-9.,&-’()]+$/                                                                                           |
| currency          | `three_letter_currency_code`                                                                                       |
| beneficiary\_type | Must be either `business` or `individual`                                                                          |
| bank\_name        | -                                                                                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i                                                                 |
| iban              | /^(\[A-Z]{2}\[ -]?\[0-9]{2})(?=(?:\[ -]?\[A-Z0-9]){9,30}$)((?:\[ -]?\[A-Z0-9]{3,5}){2,7})(\[ -]?\[A-Z0-9]{1,3})?$/ |

### GBP Field Validations

| Field             | Regex                                                                                                              |
| ----------------- | ------------------------------------------------------------------------------------------------------------------ |
| address\_line1    | -                                                                                                                  |
| city              | -                                                                                                                  |
| postal\_code      | -                                                                                                                  |
| country           | ISO 3166-1 alpha-2 format                                                                                          |
| account\_name     | /^\[A-Za-z0-9.,&-’()]+$/                                                                                           |
| currency          | `three_letter_currency_code`                                                                                       |
| beneficiary\_type | Must be either `business` or `individual`                                                                          |
| bank\_name        | -                                                                                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i                                                                 |
| iban              | /^(\[A-Z]{2}\[ -]?\[0-9]{2})(?=(?:\[ -]?\[A-Z0-9]){9,30}$)((?:\[ -]?\[A-Z0-9]{3,5}){2,7})(\[ -]?\[A-Z0-9]{1,3})?$/ |

### USD Field Validations

| Field             | Regex                                     |
| ----------------- | ----------------------------------------- |
| address\_line1    | -                                         |
| city              | -                                         |
| postal\_code      | -                                         |
| country           | ISO 3166-1 alpha-2 format                 |
| account\_name     | /^\[A-Za-z0-9.,&-’()]{1,35}$/             |
| currency          | `three_letter_currency_code`              |
| beneficiary\_type | Must be either `business` or `individual` |
| bank\_name        | -                                         |
| routing\_number   | /^\d{9}$/                                 |
| account\_number   | /^\[\da-zA-Z]{6,17}$/                     |
