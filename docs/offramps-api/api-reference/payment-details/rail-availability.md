---
description: How and when to use SWIFT or Wire over local rails
---

# Rail Availability

To make a payment over faster, cheaper local rails (such as ACH in the US or SEPA in Europe), [create a Payment Detail](paymentdetails-create.md#create-a-payment-detail) with `rails` set to **local** and [create your Offramp](../offramps/offramps-create.md) against that Payment Detail with rails set to **local** as well.

If the account you wish to pay is not on local rails - for example it is a USD bank account in Singapore - then you will have to use the SWIFT network. When you create the Payment Details set the `rails` attribute to **swift** and when you create an Offramp against that Payment Detail, set `rails` to **swift** there as well.\
\
For USD payments, we also support a fast, if slightly more expensive 'Wire' option as well.

### Local Rails, SWIFT, and Wire

{% hint style="info" %}
When creating a [payment\_detail](paymentdetails-create.md) for the following currencies, the value for "rails" can be **local** when you want to use SEPA/ACH rails, **swift** when you want to use SWIFT rails, or **wire** for a domestic wire payment. Wire is faster than ACH (0-1 business days as opposed to 3) but has a surcharge of $20.
{% endhint %}

| Currency |
| -------- |
| usd      |

### Local Rails & SWIFT

{% hint style="info" %}
When creating a [payment\_detail](paymentdetails-create.md) for the following currencies, the value for "rails" can be **local** when you want to use SEPA/ACH rails, and **swift** when you want to use SWIFT rails. Generally, if the bank account you are paying supports SEPA/ACH, you should set "rails" as **local** to enjoy faster delivery time and lower rates.
{% endhint %}

| Currency |
| -------- |
| eur      |

### Local Rails Only

{% hint style="info" %}
When creating a [payment\_detail](paymentdetails-create.md) for the following currecnies, the value for "rails" must be **local,** as SWIFT is not supported for the currency.
{% endhint %}

| Currency |
| -------- |
| ars      |
| bob      |
| brl      |
| clp      |
| cop      |
| crc      |
| dop      |
| ghs      |
| gtq      |
| hnl      |
| kes      |
| mxn      |
| mzn      |
| ngn      |
| pen      |
| pyg      |
| ugx      |
| uyu      |
| zar      |
| zwl      |

### SWIFT Only

{% hint style="info" %}
For the following currencies. When creating a [payment\_detail](paymentdetails-create.md), the value for "rails" must be **swift** as only SWIFT payments are supported for these currencies.
{% endhint %}

| Currency |
| -------- |
| aed      |
| aud      |
| cad      |
| chf      |
| cny      |
| gbp      |
| hkd      |
| idr      |
| inr      |
| inr      |
| jpy      |
| myr      |
| nzd      |
| php      |
| pln      |
| sgd      |
| thb      |
| xaf      |
| xof      |
