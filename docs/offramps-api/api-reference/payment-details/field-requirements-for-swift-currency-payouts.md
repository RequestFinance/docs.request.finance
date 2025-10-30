# Field Requirements For Swift Currency Payouts

The following currencies are available for SWIFT payouts. Please note our [Required Fields For All Currencies Section](field-requirements-for-swift-currency-payouts.md#required-fields-for-all-currencies)

* [United Arab Emirates Dirham (AED)](field-requirements-for-swift-currency-payouts.md#additional-aed-swift-fields)
* [Australian Dollar (AUD)](field-requirements-for-swift-currency-payouts.md#additional-aud-swift-fields)
* [Canadian Dollar (CAD)](field-requirements-for-swift-currency-payouts.md#additional-cad-swift-fields)
* [Swiss Franc (CHF)](field-requirements-for-swift-currency-payouts.md#additional-chf-swift-fields)
* [Chinese Yuan (CNY)](field-requirements-for-swift-currency-payouts.md#additional-cnyy-swift-fields)
* [Euro (EUR)](field-requirements-for-swift-currency-payouts.md#additional-eur-swift-fields)
* [Great British Pound (GBP)](field-requirements-for-swift-currency-payouts.md#additional-gbp-swift-fields)
* [Hong Kong Dollar (HKD)](field-requirements-for-swift-currency-payouts.md#additional-hkd-swift-fields)
* [Indonesian Rupiah (IDR)](field-requirements-for-swift-currency-payouts.md#additional-idr-swift-fields)
* [Indian Rupee (INR)](field-requirements-for-swift-currency-payouts.md#additional-inr-swift-fields)
* [Japanese Yen (JPY)](field-requirements-for-swift-currency-payouts.md#additional-jpy-swift-fields)
* [South Korean Won (KRW)](field-requirements-for-swift-currency-payouts.md#additional-krw-swift-fields)
* [Malaysian Ringgit (MYR)](field-requirements-for-swift-currency-payouts.md#additional-myr-swift-fields)
* [New Zealand Dollar (NZD)](field-requirements-for-swift-currency-payouts.md#additional-nzd-swift-fields)
* [Philippine Peso (PHP)](field-requirements-for-swift-currency-payouts.md#additional-php-swift-fields)
* [Polish Zloty (PLN)](field-requirements-for-swift-currency-payouts.md#additional-pln-swift-fields)
* [Singapore Dollar (SGD)](field-requirements-for-swift-currency-payouts.md#additional-sgd-swift-fields)
* [Thai Baht (THB)](field-requirements-for-swift-currency-payouts.md#additional-thb-swift-fields)
* [United States Dollar (USD)](field-requirements-for-swift-currency-payouts.md#additional-usd-swift-fields)

### Required Fields For All Currencies

{% hint style="info" %}
Please ensure that you supply the following bank account information for **every** payment\_detail you create.
{% endhint %}

| Field             | Regex                                     |
| ----------------- | ----------------------------------------- |
| address\_line1    | -                                         |
| city              | -                                         |
| postal\_code      | -                                         |
| country           | ISO 3166-1 alpha-2 format                 |
| account\_name     | -                                         |
| currency          | `three_letter_currency_code`              |
| beneficiary\_type | Must be either `business` or `individual` |
| bank\_name        | -                                         |

### Additional AED Swift Fields

| Field      | Regex |
| ---------- | ----- |
| swift\_bic |       |
| iban       |       |

### Additional AUD Swift Fields

| Field           | Regex                                              |
| --------------- | -------------------------------------------------- |
| swift\_bic      | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| bsb\_number     | /^\d{3}-?\d{3}$/                                   |
| account\_number | /^\d{6,25}$/                                       |

### Additional CAD Swift Fields

| Field           | Regex                                              |
| --------------- | -------------------------------------------------- |
| swift\_bic      | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| bank\_code      |                                                    |
| branch\_code    |                                                    |
| account\_number | /^\d{6,25}$/                                       |

### Additional CHF Swift Fields

| Field      | Regex                                                                                                              |
| ---------- | ------------------------------------------------------------------------------------------------------------------ |
| swift\_bic | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i                                                                 |
| iban       | /^(\[A-Z]{2}\[ -]?\[0-9]{2})(?=(?:\[ -]?\[A-Z0-9]){9,30}$)((?:\[ -]?\[A-Z0-9]{3,5}){2,7})(\[ -]?\[A-Z0-9]{1,3})?$/ |

### Additional CNY Swift Fields

| Field           | Regex                                              |
| --------------- | -------------------------------------------------- |
| swift\_bic      | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number | /^\d{6,25}$/                                       |

### Additional EUR Swift Fields

| Field      | Regex                                                                                                              | Notes                                      |
| ---------- | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------ |
| swift\_bic | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i                                                                 | Only required if `rails` is set to `swift` |
| iban       | /^(\[A-Z]{2}\[ -]?\[0-9]{2})(?=(?:\[ -]?\[A-Z0-9]){9,30}$)((?:\[ -]?\[A-Z0-9]{3,5}){2,7})(\[ -]?\[A-Z0-9]{1,3})?$/ |                                            |

### Additional GBP Swift Fields

| Field      | Regex                                                                                                              |
| ---------- | ------------------------------------------------------------------------------------------------------------------ |
| swift\_bic | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i                                                                 |
| iban       | /^(\[A-Z]{2}\[ -]?\[0-9]{2})(?=(?:\[ -]?\[A-Z0-9]){9,30}$)((?:\[ -]?\[A-Z0-9]{3,5}){2,7})(\[ -]?\[A-Z0-9]{1,3})?$/ |

### Additional HKD Swift Fields

| Field           | Regex                                              |
| --------------- | -------------------------------------------------- |
| swift\_bic      | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number | /^\d{6,25}$/                                       |
| bank\_code      |                                                    |

### Additional IDR SWIFT Fields

| Field           | Regex                                              |
| --------------- | -------------------------------------------------- |
| swift\_bic      | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| bank\_code      | -                                                  |
| account\_number | /^\d{6,25}$/                                       |

### Additional INR SWIFT Fields

| Field           | Regex                                              |
| --------------- | -------------------------------------------------- |
| swift\_bic      | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| bank\_code      | -                                                  |
| account\_number | /^\d{6,25}$/                                       |
| ifsc            | /^(?=.\[0-9])(?=.\[a-zA-Z])\[a-zA-Z0-9]{11}$/      |

### Additional JPY SWIFT Fields

| Field           | Regex                                              |
| --------------- | -------------------------------------------------- |
| swift\_bic      | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number | /^\d{6,25}$/                                       |

### Additional KRW SWIFT Fields

| Field           | Regex                                              |
| --------------- | -------------------------------------------------- |
| swift\_bic      | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number | /^\d{6,25}$/                                       |
| bank\_code      |                                                    |

### Additional MYR SWIFT Fields

| Field           | Regex                                              |
| --------------- | -------------------------------------------------- |
| swift\_bic      | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number | /^\d{6,25}$/                                       |

### Additional NZD SWIFT Fields

| Field           | Regex                                              |
| --------------- | -------------------------------------------------- |
| swift\_bic      | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number | /^\d{6,25}$/                                       |
| ncc             |                                                    |

### Additional PHP SWIFT Fields

| Field           | Regex                                              |
| --------------- | -------------------------------------------------- |
| swift\_bic      | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number | /^\d{6,25}$/                                       |

### Additional PLN SWIFT Fields

| Field      | Regex                                                                                                              |
| ---------- | ------------------------------------------------------------------------------------------------------------------ |
| swift\_bic | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i                                                                 |
| iban       | /^(\[A-Z]{2}\[ -]?\[0-9]{2})(?=(?:\[ -]?\[A-Z0-9]){9,30}$)((?:\[ -]?\[A-Z0-9]{3,5}){2,7})(\[ -]?\[A-Z0-9]{1,3})?$/ |

### Additional SGD SWIFT Fields

| Field           | Regex                                              |
| --------------- | -------------------------------------------------- |
| swift\_bic      | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number | /^\d{6,25}$/                                       |

### Additional THB SWIFT Fields

| Field           | Regex                                              |
| --------------- | -------------------------------------------------- |
| swift\_bic      | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number | /^\d{6,25}$/                                       |

### Additional USD SWIFT Fields

| Field           | Regex                                                                                                              | Notes                                                                                                              |
| --------------- | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| account\_number | /^\[\da-zA-Z]{6,25}$/                                                                                              |                                                                                                                    |
| routing\_number | /^\d{9}$/                                                                                                          |                                                                                                                    |
| swift\_bic      | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i                                                                 | Only required if `rails` is set to `swift`                                                                         |
| iban            | /^(\[A-Z]{2}\[ -]?\[0-9]{2})(?=(?:\[ -]?\[A-Z0-9]){9,30}$)((?:\[ -]?\[A-Z0-9]{3,5}){2,7})(\[ -]?\[A-Z0-9]{1,3})?$/ | Can be sent instead of `account_number` if `account_number` is not provided by the users bank. Common for `swift.` |

