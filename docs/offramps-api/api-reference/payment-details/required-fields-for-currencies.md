---
hidden: true
---

# Required Fields For Currencies

### Currency

* [United Arab Emirates Dirham (AED)](required-fields-for-currencies.md#aed)
* [Argentine Peso (ARS)](required-fields-for-currencies.md#ars)
* [Australian Dollar (AUD)](required-fields-for-currencies.md#aud)
* [Canadian Dollar (CAD)](required-fields-for-currencies.md#cad)
* [Swiss Franc (CHF)](required-fields-for-currencies.md#chf)
* [Chinese Yuan (CNY)](required-fields-for-currencies.md#cny)
* [Chilean Peso (CLP)](required-fields-for-currencies.md#clp)
* [Colombian Peso (COP)](required-fields-for-currencies.md#cop-rails-koywe-recommended)
* [Euro (EUR)](required-fields-for-currencies.md#eur)
* [Hong Kong Dollar (HKD)](required-fields-for-currencies.md#hkd)
* [Indonesian Rupiah (IDR)](required-fields-for-currencies.md#idr)
* [Indian Rupee (INR)](required-fields-for-currencies.md#inr)
* [Japanese Yen (JPY)](required-fields-for-currencies.md#jpy)
* [Peruvian Sol (PEN)](required-fields-for-currencies.md#sol)
* [South Korean Won (KRW)](required-fields-for-currencies.md#krw)
* [Mexican Peso (MXN)](required-fields-for-currencies.md#mxn)
* [Malaysian Ringgit (MYR)](required-fields-for-currencies.md#myr)
* [New Zealand Dollar (NZD)](required-fields-for-currencies.md#nzd)
* [Philippine Peso (PHP)](required-fields-for-currencies.md#php)
* [Polish Zloty (PLN)](required-fields-for-currencies.md#pln)
* [Singapore Dollar (SGD)](required-fields-for-currencies.md#sgd)
* [Thai Baht (THB)](required-fields-for-currencies.md#thb)
* [United States Dollar (USD)](required-fields-for-currencies.md#usd)

NB: Any regex with a `-` value indicates that it is required to be present. But is not ran through a regex check.

### AED

| Field             | Regex                                                                                                              |
| ----------------- | ------------------------------------------------------------------------------------------------------------------ |
| address\_line1    | -                                                                                                                  |
| city              | -                                                                                                                  |
| postal\_code      | -                                                                                                                  |
| country           | ISO 3166-1 alpha-2 format                                                                                          |
| account\_name     | -                                                                                                                  |
| currency          | `aed`                                                                                                              |
| beneficiary\_type | Must be either `business` or `individual`                                                                          |
| bank\_name        | -                                                                                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i                                                                 |
| iban              | /^(\[A-Z]{2}\[ -]?\[0-9]{2})(?=(?:\[ -]?\[A-Z0-9]){9,30}$)((?:\[ -]?\[A-Z0-9]{3,5}){2,7})(\[ -]?\[A-Z0-9]{1,3})?$/ |

### ARS

| Field             | Regex                                                                                                                                                                                         |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| address\_line1    | -                                                                                                                                                                                             |
| city              | -                                                                                                                                                                                             |
| postal\_code      | -                                                                                                                                                                                             |
| country           | ISO 3166-1 alpha-2 format                                                                                                                                                                     |
| account\_name     | -                                                                                                                                                                                             |
| currency          | `ars`                                                                                                                                                                                         |
| beneficiary\_type | Must be either `business` or `individual`                                                                                                                                                     |
| bank\_name        | See [paymentdetails-latambanknames.md](paymentdetails-latambanknames.md "mention") - Bank names must _exactly_ match one of the banks provided in the response of the LatamBankNames endpoint |
| account\_number   | /^\[0-9]{22}$/                                                                                                                                                                                |
| account\_type     | Must be either `checking` or `savings`                                                                                                                                                        |
| document\_number  | /^\[0-9]{8,12}$/                                                                                                                                                                              |

### AUD

| Field             | Regex                                              |
| ----------------- | -------------------------------------------------- |
| address\_line1    | -                                                  |
| city              | -                                                  |
| postal\_code      | -                                                  |
| country           | ISO 3166-1 alpha-2 format                          |
| account\_name     | -                                                  |
| currency          | `aud`                                              |
| beneficiary\_type | Must be either `business` or `individual`          |
| bank\_name        | -                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| bsb\_number       | /^\d{3}-?\d{3}$/                                   |
| account\_number   | /^\d{6,25}$/                                       |

### CAD

| Field             | Regex                                              |
| ----------------- | -------------------------------------------------- |
| address\_line1    | -                                                  |
| city              | -                                                  |
| postal\_code      | -                                                  |
| country           | ISO 3166-1 alpha-2 format                          |
| account\_name     | -                                                  |
| currency          | `cad`                                              |
| beneficiary\_type | Must be either `business` or `individual`          |
| bank\_name        | -                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| bank\_code        |                                                    |
| branch\_code      |                                                    |
| account\_number   | /^\d{6,25}$/                                       |

### CHF

| Field             | Regex                                                                                                              |
| ----------------- | ------------------------------------------------------------------------------------------------------------------ |
| address\_line1    | -                                                                                                                  |
| city              | -                                                                                                                  |
| postal\_code      | -                                                                                                                  |
| country           | ISO 3166-1 alpha-2 format                                                                                          |
| account\_name     | -                                                                                                                  |
| currency          | `chf`                                                                                                              |
| beneficiary\_type | Must be either `business` or `individual`                                                                          |
| bank\_name        | -                                                                                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i                                                                 |
| iban              | /^(\[A-Z]{2}\[ -]?\[0-9]{2})(?=(?:\[ -]?\[A-Z0-9]){9,30}$)((?:\[ -]?\[A-Z0-9]{3,5}){2,7})(\[ -]?\[A-Z0-9]{1,3})?$/ |

### CNY

| Field             | Regex                                              |
| ----------------- | -------------------------------------------------- |
| address\_line1    | -                                                  |
| city              | -                                                  |
| postal\_code      | -                                                  |
| country           | ISO 3166-1 alpha-2 format                          |
| account\_name     | -                                                  |
| currency          | `cny`                                              |
| beneficiary\_type | Must be either `business` or `individual`          |
| bank\_name        | -                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number   | /^\d{6,25}$/                                       |

### CLP

| Field             | Regex                                                                                                                                                                                                                                |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| address\_line1    | -                                                                                                                                                                                                                                    |
| city              | -                                                                                                                                                                                                                                    |
| postal\_code      | -                                                                                                                                                                                                                                    |
| country           | ISO 3166-1 alpha-2 format                                                                                                                                                                                                            |
| account\_name     | -                                                                                                                                                                                                                                    |
| currency          | `clp`                                                                                                                                                                                                                                |
| beneficiary\_type | Must be either `business` or `individual`                                                                                                                                                                                            |
| bank\_name        | See [paymentdetails-latambanknames.md](paymentdetails-latambanknames.md "mention") - Bank names must _exactly_ match one of the banks provided in the response of the LatamBankNames endpoint                                        |
| document\_type    | `rut`                                                                                                                                                                                                                                |
| document\_number  | -                                                                                                                                                                                                                                    |
| phone             | -                                                                                                                                                                                                                                    |
| neighbourhood     | -                                                                                                                                                                                                                                    |
| date\_of\_birth   | -                                                                                                                                                                                                                                    |
| activity          | -                                                                                                                                                                                                                                    |
| nationality       | Required for **individuals** only, must be one of the following values: `[AG AR BS BB BZ BO BR CA CL CO CR CU DM DO EC SV GD GT GY HT HN JM MX NI PA PY PE PR KN LC VC SR TT US UY VE AI AW BM BQ KY GS GL GP FK MQ MS AN TC VG VI]` |
| gender            | Required for **individuals** only, must be one of the following values: `o` `m` `f`                                                                                                                                                  |

### COP - rails "koywe" (recommended)

| Field             | Regex                                                                                                                                                                                                                            |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| address\_line1    | -                                                                                                                                                                                                                                |
| city              | -                                                                                                                                                                                                                                |
| postal\_code      | -                                                                                                                                                                                                                                |
| country           | ISO 3166-1 alpha-2 format                                                                                                                                                                                                        |
| account\_name     | -                                                                                                                                                                                                                                |
| currency          | `cop`                                                                                                                                                                                                                            |
| beneficiary\_type | Must be either `business` or `individual`                                                                                                                                                                                        |
| bank\_name        | See [paymentdetails-latambanknames.md](paymentdetails-latambanknames.md "mention") - Bank names must _exactly_ match one of the banks provided in the response of the LatamBankNames endpoint                                    |
| document\_type    | <p>For individuals the accepted values are: <code>ced_ciu</code> and <code>ced_ext</code><br>For businesses the accepted values are: <code>nit</code></p>                                                                        |
| document\_number  | -                                                                                                                                                                                                                                |
| phone             | -                                                                                                                                                                                                                                |
| account\_type     | Must be one of the following values: `checking` `savings`                                                                                                                                                                        |
| neighbourhood     | -                                                                                                                                                                                                                                |
| date\_of\_birth   | -                                                                                                                                                                                                                                |
| activity          | -                                                                                                                                                                                                                                |
| nationality       | Required for individuals only, must be one of the following values: `[AG AR BS BB BZ BO BR CA CL CO CR CU DM DO EC SV GD GT GY HT HN JM MX NI PA PY PE PR KN LC VC SR TT US UY VE AI AW BM BQ KY GS GL GP FK MQ MS AN TC VG VI]` |
| gender            | Required for individuals only, must be one of the following values: `o` `m` `f`                                                                                                                                                  |
| rails             | Must be `koywe`                                                                                                                                                                                                                  |

### COP - rails "local"

{% hint style="warning" %}
This rail will be deprecated, please use COP - rails "koywe" instead.
{% endhint %}

| Field             | Regex                                                                                                                                                                                         |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| address\_line1    | -                                                                                                                                                                                             |
| city              | -                                                                                                                                                                                             |
| postal\_code      | -                                                                                                                                                                                             |
| country           | ISO 3166-1 alpha-2 format                                                                                                                                                                     |
| account\_name     | -                                                                                                                                                                                             |
| currency          | `cop`                                                                                                                                                                                         |
| beneficiary\_type | Must be either `business` or `individual`                                                                                                                                                     |
| bank\_name        | See [paymentdetails-latambanknames.md](paymentdetails-latambanknames.md "mention") - Bank names must _exactly_ match one of the banks provided in the response of the LatamBankNames endpoint |
| document\_type    | Must be one of the following values: `national_id` `ruc` `passport` `resident_id`                                                                                                             |
| document\_number  | /^\d{1,15}$/                                                                                                                                                                                  |
| phone             | -                                                                                                                                                                                             |
| account\_number   | /^\d{6,25}$/                                                                                                                                                                                  |
| account\_type     | Must be one of the following values: `checking` `savings`                                                                                                                                     |
| rails             | Must be one of the following values: `nil`, `local`                                                                                                                                           |

### EUR

| Field             | Regex                                                                                                              | Notes                                      |
| ----------------- | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------ |
| address\_line1    | -                                                                                                                  |                                            |
| city              | -                                                                                                                  |                                            |
| postal\_code      | -                                                                                                                  |                                            |
| country           | ISO 3166-1 alpha-2 format                                                                                          |                                            |
| account\_name     | -                                                                                                                  |                                            |
| currency          | `eur`                                                                                                              |                                            |
| beneficiary\_type | Must be either `business` or `individual`                                                                          |                                            |
| bank\_name        | -                                                                                                                  |                                            |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i                                                                 | Only required if `rails` is set to `swift` |
| iban              | /^(\[A-Z]{2}\[ -]?\[0-9]{2})(?=(?:\[ -]?\[A-Z0-9]){9,30}$)((?:\[ -]?\[A-Z0-9]{3,5}){2,7})(\[ -]?\[A-Z0-9]{1,3})?$/ |                                            |

### GBP

| Field             | Regex                                                                                                              |
| ----------------- | ------------------------------------------------------------------------------------------------------------------ |
| address\_line1    | -                                                                                                                  |
| city              | -                                                                                                                  |
| postal\_code      | -                                                                                                                  |
| country           | ISO 3166-1 alpha-2 format                                                                                          |
| account\_name     | -                                                                                                                  |
| currency          | `gbp`                                                                                                              |
| beneficiary\_type | Must be either `business` or `individual`                                                                          |
| bank\_name        | -                                                                                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i                                                                 |
| iban              | /^(\[A-Z]{2}\[ -]?\[0-9]{2})(?=(?:\[ -]?\[A-Z0-9]){9,30}$)((?:\[ -]?\[A-Z0-9]{3,5}){2,7})(\[ -]?\[A-Z0-9]{1,3})?$/ |

### HKD

| Field             | Regex                                              |
| ----------------- | -------------------------------------------------- |
| address\_line1    | -                                                  |
| city              | -                                                  |
| postal\_code      | -                                                  |
| country           | ISO 3166-1 alpha-2 format                          |
| account\_name     | -                                                  |
| currency          | `hkd`                                              |
| beneficiary\_type | Must be either `business` or `individual`          |
| bank\_name        | -                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number   | /^\d{6,25}$/                                       |
| bank\_code        |                                                    |

### IDR

| Field             | Regex                                              |
| ----------------- | -------------------------------------------------- |
| address\_line1    | -                                                  |
| city              | -                                                  |
| postal\_code      | -                                                  |
| country           | ISO 3166-1 alpha-2 format                          |
| account\_name     | -                                                  |
| currency          | `idr`                                              |
| beneficiary\_type | Must be either `business` or `individual`          |
| bank\_name        | -                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| bank\_code        | -                                                  |
| account\_number   | /^\d{6,25}$/                                       |

### INR

| Field             | Regex                                              |
| ----------------- | -------------------------------------------------- |
| address\_line1    | -                                                  |
| city              | -                                                  |
| postal\_code      | -                                                  |
| country           | ISO 3166-1 alpha-2 format                          |
| account\_name     | -                                                  |
| currency          | `inr`                                              |
| beneficiary\_type | Must be either `business` or `individual`          |
| bank\_name        | -                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| bank\_code        | -                                                  |
| account\_number   | /^\d{6,25}$/                                       |
| ifsc              | /^(?=.\[0-9])(?=.\[a-zA-Z])\[a-zA-Z0-9]{11}$/      |

### JPY

| Field             | Regex                                              |
| ----------------- | -------------------------------------------------- |
| address\_line1    | -                                                  |
| city              | -                                                  |
| postal\_code      | -                                                  |
| country           | ISO 3166-1 alpha-2 format                          |
| account\_name     | -                                                  |
| currency          | `jpy`                                              |
| beneficiary\_type | Must be either `business` or `individual`          |
| bank\_name        | -                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number   | /^\d{6,25}$/                                       |

### KRW

| Field             | Regex                                              |
| ----------------- | -------------------------------------------------- |
| address\_line1    | -                                                  |
| city              | -                                                  |
| postal\_code      | -                                                  |
| country           | ISO 3166-1 alpha-2 format                          |
| account\_name     | -                                                  |
| currency          | `krw`                                              |
| beneficiary\_type | Must be either `business` or `individual`          |
| bank\_name        | -                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number   | /^\d{6,25}$/                                       |
| bank\_code        |                                                    |

### MXN

| Field             | Regex                                                                                                                                                                                                                                |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| address\_line1    | -                                                                                                                                                                                                                                    |
| city              | -                                                                                                                                                                                                                                    |
| postal\_code      | -                                                                                                                                                                                                                                    |
| country           | ISO 3166-1 alpha-2 format                                                                                                                                                                                                            |
| account\_name     | -                                                                                                                                                                                                                                    |
| currency          | `mxn`                                                                                                                                                                                                                                |
| beneficiary\_type | Must be either `business` or `individual`                                                                                                                                                                                            |
| bank\_name        | See [paymentdetails-latambanknames.md](paymentdetails-latambanknames.md "mention") - Bank names must _exactly_ match one of the banks provided in the response of the LatamBankNames endpoint                                        |
| document\_type    | For individuals the accepted values are: `curp`. For businesses the accepted values are: `rfc`                                                                                                                                       |
| document\_number  | -                                                                                                                                                                                                                                    |
| phone             | -                                                                                                                                                                                                                                    |
| neighbourhood     | -                                                                                                                                                                                                                                    |
| date\_of\_birth   | -                                                                                                                                                                                                                                    |
| activity          | -                                                                                                                                                                                                                                    |
| nationality       | Required for **individuals** only, must be one of the following values: `[AG AR BS BB BZ BO BR CA CL CO CR CU DM DO EC SV GD GT GY HT HN JM MX NI PA PY PE PR KN LC VC SR TT US UY VE AI AW BM BQ KY GS GL GP FK MQ MS AN TC VG VI]` |
| gender            | Required for **individuals** only, must be one of the following values: `o` `m` `f`                                                                                                                                                  |

### MYR

| Field             | Regex                                              |
| ----------------- | -------------------------------------------------- |
| address\_line1    | -                                                  |
| city              | -                                                  |
| postal\_code      | -                                                  |
| country           | ISO 3166-1 alpha-2 format                          |
| account\_name     | -                                                  |
| currency          | `myr`                                              |
| beneficiary\_type | Must be either `business` or `individual`          |
| bank\_name        | -                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number   | /^\d{6,25}$/                                       |

### NZD

| Field             | Regex                                              |
| ----------------- | -------------------------------------------------- |
| address\_line1    | -                                                  |
| city              | -                                                  |
| postal\_code      | -                                                  |
| country           | ISO 3166-1 alpha-2 format                          |
| account\_name     | -                                                  |
| currency          | `nzd`                                              |
| beneficiary\_type | Must be either `business` or `individual`          |
| bank\_name        | -                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number   | /^\d{6,25}$/                                       |
| ncc               |                                                    |

### PHP

| Field             | Regex                                              |
| ----------------- | -------------------------------------------------- |
| address\_line1    | -                                                  |
| city              | -                                                  |
| postal\_code      | -                                                  |
| country           | ISO 3166-1 alpha-2 format                          |
| account\_name     | -                                                  |
| currency          | `php`                                              |
| beneficiary\_type | Must be either `business` or `individual`          |
| bank\_name        | -                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number   | /^\d{6,25}$/                                       |

### PLN

| Field             | Regex                                                                                                              |
| ----------------- | ------------------------------------------------------------------------------------------------------------------ |
| address\_line1    | -                                                                                                                  |
| city              | -                                                                                                                  |
| postal\_code      | -                                                                                                                  |
| country           | ISO 3166-1 alpha-2 format                                                                                          |
| account\_name     | -                                                                                                                  |
| currency          | `pln`                                                                                                              |
| beneficiary\_type | Must be either `business` or `individual`                                                                          |
| bank\_name        | -                                                                                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i                                                                 |
| iban              | /^(\[A-Z]{2}\[ -]?\[0-9]{2})(?=(?:\[ -]?\[A-Z0-9]){9,30}$)((?:\[ -]?\[A-Z0-9]{3,5}){2,7})(\[ -]?\[A-Z0-9]{1,3})?$/ |

### SGD

| Field             | Regex                                              |
| ----------------- | -------------------------------------------------- |
| address\_line1    | -                                                  |
| city              | -                                                  |
| postal\_code      | -                                                  |
| country           | ISO 3166-1 alpha-2 format                          |
| account\_name     | -                                                  |
| currency          | `sgd`                                              |
| beneficiary\_type | Must be either `business` or `individual`          |
| bank\_name        | -                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number   | /^\d{6,25}$/                                       |

### SOL

| Field             | Regex                                                                                                                                                                                                                                |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| address\_line1    | -                                                                                                                                                                                                                                    |
| city              | -                                                                                                                                                                                                                                    |
| postal\_code      | -                                                                                                                                                                                                                                    |
| country           | ISO 3166-1 alpha-2 format                                                                                                                                                                                                            |
| account\_name     | -                                                                                                                                                                                                                                    |
| currency          | `pen`                                                                                                                                                                                                                                |
| beneficiary\_type | Must be either `business` or `individual`                                                                                                                                                                                            |
| bank\_name        | See [paymentdetails-latambanknames.md](paymentdetails-latambanknames.md "mention") - Bank names must _exactly_ match one of the banks provided in the response of the LatamBankNames endpoint                                        |
| document\_type    | For individuals the accepted values are: `dni`. For businesses the accepted values are: `ruc`                                                                                                                                        |
| document\_number  | -                                                                                                                                                                                                                                    |
| phone             | -                                                                                                                                                                                                                                    |
| neighbourhood     | -                                                                                                                                                                                                                                    |
| date\_of\_birth   | -                                                                                                                                                                                                                                    |
| activity          | -                                                                                                                                                                                                                                    |
| nationality       | Required for **individuals** only, must be one of the following values: `[AG AR BS BB BZ BO BR CA CL CO CR CU DM DO EC SV GD GT GY HT HN JM MX NI PA PY PE PR KN LC VC SR TT US UY VE AI AW BM BQ KY GS GL GP FK MQ MS AN TC VG VI]` |
| gender            | Required for **individuals** only, must be one of the following values: `o` `m` `f`                                                                                                                                                  |

### THB

| Field             | Regex                                              |
| ----------------- | -------------------------------------------------- |
| address\_line1    | -                                                  |
| city              | -                                                  |
| postal\_code      | -                                                  |
| country           | ISO 3166-1 alpha-2 format                          |
| account\_name     | -                                                  |
| currency          | `thb`                                              |
| beneficiary\_type | Must be either `business` or `individual`          |
| bank\_name        | -                                                  |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i |
| account\_number   | /^\d{6,25}$/                                       |

### USD

| Field             | Regex                                                                                                              | Notes                                                                                                              |
| ----------------- | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| address\_line1    | -                                                                                                                  |                                                                                                                    |
| city              | -                                                                                                                  |                                                                                                                    |
| postal\_code      | -                                                                                                                  |                                                                                                                    |
| country           | ISO 3166-1 alpha-2 format                                                                                          |                                                                                                                    |
| account\_name     | -                                                                                                                  |                                                                                                                    |
| currency          | `usd`                                                                                                              |                                                                                                                    |
| beneficiary\_type | Must be either `business` or `individual`                                                                          |                                                                                                                    |
| bank\_name        | -                                                                                                                  |                                                                                                                    |
| account\_number   | /^\[\da-zA-Z]{6,25}$/                                                                                              |                                                                                                                    |
| routing\_number   | /^\d{9}$/                                                                                                          |                                                                                                                    |
| swift\_bic        | /^\[a-zA-Z]{6}\[a-zA-Z0-9]{2}(\[a-zA-Z0-9]{3})?$/i                                                                 | Only required if `rails` is set to `swift`                                                                         |
| iban              | /^(\[A-Z]{2}\[ -]?\[0-9]{2})(?=(?:\[ -]?\[A-Z0-9]){9,30}$)((?:\[ -]?\[A-Z0-9]{3,5}){2,7})(\[ -]?\[A-Z0-9]{1,3})?$/ | Can be sent instead of `account_number` if `account_number` is not provided by the users bank. Common for `swift.` |

