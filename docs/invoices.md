# Invoices

To get paid in cryptocurrency, you first need to create an invoice, which includes details on the buyer, the product or service purchased, the price, taxes, and how you would like to get paid.

After creating the invoice off-chain, it needs to be converted into an on-chain request using another endpoint introduced further below.

{% hint style="info" %}
The Request Network protocol is all about creating payment requests. They are stored on-chain. Invoices are what you will be manipulating with the Request Finance API. Invoices are simply an implementation of requests with a predefined schema for their content. If you wish to learn more about this, please visit [this page](faq.md#how-do-requests-and-invoices-differ-from-each-other).
{% endhint %}

## Creating an Off-Chain Invoice

## Creates an off-chain invoice for the account

<mark style="color:green;">`POST`</mark> `https://api.request.finance/invoices`

#### Request Body

| Name                                                     | Type                        | Description                                                                                                                                                                                                                                                                                                                                                                                          |
| -------------------------------------------------------- | --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| meta                                                     | Request Network JSON Schema | <p>Format of the underlying request. Refer to the <a href="https://github.com/RequestNetwork/requestNetwork/tree/master/packages/data-format#available-json-schema">Request Network protocol documentation</a> for all possible values.<br><br>Default value:<br><code>{</code></p><p><code>format: "rnf_invoice",</code></p><p><code>version: "0.0.3",</code></p><p><code>}</code></p>              |
| creationDate                                             | String                      | <p>ISO-8601 representation of the invoice’s creation date.<br><br>Default value:<br>Current date</p>                                                                                                                                                                                                                                                                                                 |
| invoiceItems.currency<mark style="color:red;">\*</mark>  | String                      | Currency code in which the invoice is denominated. For example, invoices can be denominated in USD, but buyers can pay in crypto.                                                                                                                                                                                                                                                                    |
| invoiceItems.name                                        | String                      | Name of the product/service for which the invoice is created.                                                                                                                                                                                                                                                                                                                                        |
| invoiceItems.quantity<mark style="color:red;">\*</mark>  | Decimal                     | Quantity of the product/service that was provided.                                                                                                                                                                                                                                                                                                                                                   |
| invoiceItems.tax.type                                    | String                      | <p>Can be “fixed” or “percentage”. Required if tax.amount is sent.<br><br>Default value:<br><code>fixed</code></p>                                                                                                                                                                                                                                                                                   |
| invoiceItems.tax.amount                                  | Decimal                     | <p>Amount of the tax. Required if tax.type is sent.<br><br>Default value:<br><code>0</code></p>                                                                                                                                                                                                                                                                                                      |
| invoiceItems.unitPrice<mark style="color:red;">\*</mark> | Integer                     | Price of the product/service, excl. taxes.                                                                                                                                                                                                                                                                                                                                                           |
| invoiceNumber<mark style="color:red;">\*</mark>          | String                      | Invoice number. Has to be unique for each invoice.                                                                                                                                                                                                                                                                                                                                                   |
| buyerInfo.businessName                                   | String                      | Business name of the buyer (the customer).                                                                                                                                                                                                                                                                                                                                                           |
| buyerInfo.address.streetAddress                          | String                      | Street, house, apartment of the buyer.                                                                                                                                                                                                                                                                                                                                                               |
| buyerInfo.address.extendedAddress                        | String                      | Extended details on the address of the buyer.                                                                                                                                                                                                                                                                                                                                                        |
| buyerInfo.address.city.postalCode                        | String                      | Post code of the buyer.                                                                                                                                                                                                                                                                                                                                                                              |
| buyerInfo.address.region                                 | String                      | Region of the buyer (e.g. “California”).                                                                                                                                                                                                                                                                                                                                                             |
| buyerInfo.address.country                                | String                      | Two character ISO 3166-1 country code of the buyer.                                                                                                                                                                                                                                                                                                                                                  |
| buyerInfo.email<mark style="color:red;">\*</mark>        | String                      | Email of the buyer.                                                                                                                                                                                                                                                                                                                                                                                  |
| buyerInfo.firstName                                      | String                      | First name (incl. middle names) of the buyer.                                                                                                                                                                                                                                                                                                                                                        |
| buyerInfo.lastName                                       | String                      | Last name of the buyer.                                                                                                                                                                                                                                                                                                                                                                              |
| buyerInfo.taxRegistration                                | String                      | Tax registration number of the buyer.                                                                                                                                                                                                                                                                                                                                                                |
| paymentTerms.dueDate                                     | String                      | ISO-8601 due date of the invoice. Last date the buyer can pay.                                                                                                                                                                                                                                                                                                                                       |
| paymentAddress<mark style="color:red;">\*</mark>         | String                      | Address which will receive the payment.                                                                                                                                                                                                                                                                                                                                                              |
| paymentCurrency<mark style="color:red;">\*</mark>        | String                      | Currency in which the invoice can be paid. Please review our [Currency API](https://api.request.finance/currency/list/invoicing) for a list of available currencies.                                                                                                                                                                                                                                 |
| note                                                     | String                      | An optionnal descriptive note.                                                                                                                                                                                                                                                                                                                                                                       |
| tags                                                     | Array of strings            | One or multiple tags for an invoice.                                                                                                                                                                                                                                                                                                                                                                 |
| recurringRule                                            | String                      | <p>Used to create a recurring invoice. Input as defined by the <a href="https://www.rfc-editor.org/rfc/rfc5545">ical RFC</a>. Recommended tool: <a href="https://jakubroztocil.github.io/rrule/">https://jakubroztocil.github.io/rrule/</a>.<br><br>Example:</p><p>DTSTART:20230314T085800Z RRULE:FREQ=MONTHLY;INTERVAL=1<br><br>Monthly on the 14th of each month, starting 14th of March 2023.</p> |

{% tabs %}
{% tab title="201: Created Off-chain invoice successfully created" %}
```json
{
    "id": "63f2f5a7f00a45f276585b27",
    "paymentCurrency": "USDC-matic",
    "buyerInfo": {
        "taxRegistration": "985-80-3313",
        "lastName": "Walton",
        "firstName": "Justin",
        "email": "justin.walton@acme-wholesaler.com",
        "businessName": "Acme Wholesaler Ltd.",
        "address": {
            "streetAddress": "4933 Oakwood Avenue",
            "extendedAddress": "",
            "city": "New York",
            "postalCode": "10038",
            "region": "New York",
            "country": "US",
            "locality": "New York",
            "country-name": "US",
            "extended-address": "",
            "postal-code": "10038",
            "street-address": "4933 Oakwood Avenue"
        },
        "userId": "63c8d2c230d75e750fb449ea"
    },
    "paymentAddress": "0x4886E85E192cdBC81d42D89256a81dAb990CDD74",
    "invoiceItems": [
        {
            "currency": "USD",
            "name": "Television",
            "quantity": 2,
            "tax": {
                "type": "percentage",
                "amount": "20"
            },
            "unitPrice": "9999"
        }
    ],
    "paymentTerms": {
        "dueDate": "2023-01-21T23:59:59.999Z"
    },
    "invoiceNumber": "3",
    "creationDate": "2022-12-22T14:38:16.916Z",
    "meta": {
        "format": "rnf_invoice",
        "version": "0.0.3"
    },
    "sellerInfo": {
        "email": "joe.bloggs@acme-seller",
        "address": {
            "streetAddress": "4933 Oakwood Avenue",
            "extendedAddress": "",
            "city": "New York",
            "postalCode": "10038",
            "region": "New York",
            "country": "US",
            "locality": "New York",
            "country-name": "US",
            "extended-address": "",
            "postal-code": "10038",
            "street-address": "4933 Oakwood Avenue"
        },
        "businessName": "Acme Corporation",
        "firstName": "Joe",
        "lastName": "Bloggs",
        "taxRegistration": "123456789",
        "userId": "63995f77f46a063ba7ac34de"
    },
    "createdBy": "63995f77f46a063ba7ac34de",
    "paymentOptions": [
        {
            "type": "wallet",
            "value": {
                "currencies": [
                    "USDC-matic"
                ],
                "paymentInformation": {
                    "paymentAddress": "0x4886E85E192cdBC81d42D89256a81dAb990CDD74",
                    "chain": "matic"
                }
            }
        }
    ],
    "type": "live",
    "role": "seller",
    "tags": [
        "my_tag"
    ]
}
```
{% endtab %}
{% endtabs %}

**Example Request**

Let’s assume you sold 2 TVs, each worth $99.99, to your customer, Acme Wholesaler Ltd. on the 22nd of December 2022. The tax is 20%, so that’s $119.99 including tax.\
The total invoice amount will thus be $239.98 (=2x $119.99) and it’s payable by the 21st of January 2023.

Your contact at Acme Wholesaler Ltd. is Justin Walton, so you want to send the invoice to his email address, justin.walton@acme-wholesaler.com.

Finally, you want to be paid in USDC on Polygon.

To create an invoice for this, you would pass the following body with the request:

<pre class="language-json"><code class="lang-json"><strong>{
</strong>   "creationDate": "2022-12-22T14:38:16.916Z",
   "invoiceItems": [
       {
           "currency": "USD",
           "name": "Television",
           "quantity": 2,
           "tax": {
               "type": "percentage",
               "amount": "20"
           },
           "unitPrice": "9999"
       }
   ],
   "invoiceNumber": "13",
   "buyerInfo": {
       "businessName": "Acme Wholesaler Ltd.",
       "address": {
           "streetAddress": "4933 Oakwood Avenue",
           "extendedAddress": "",
           "city": "New York",
           "postalCode": "10038",
           "region": "New York",
           "country": "US"
       },
       "email": "justin.walton@acme-wholesaler.com",
       "firstName": "Justin",
       "lastName": "Walton",
       "taxRegistration": "985-80-3313"
   },
   "paymentTerms": {
       "dueDate": "2023-01-21T23:59:59.999Z"
   },
   "paymentAddress": "0x4886E85E192cdBC81d42D89256a81dAb990CDD74",
   "paymentCurrency": "USDC-matic",
   "tags": [
       "my_tag"
   ]
}
</code></pre>

In the JSON response, you will get an `id` field. Please save it in a variable or your database. In the next section, you will need it to convert the invoice into an on-chain request.

## Converting an Off-Chain Invoice into an On-Chain Request

To make an invoice payable, it must be converted to an on-chain request. Once the invoice is created, convert it into an on-chain request using the endpoint below. Replace `[id]` with the ID of the invoice you saved previously. You don’t need to pass anything in the request body.

## Converts off-chain invoice into on-chain request

<mark style="color:green;">`POST`</mark> `https://api.request.finance/invoices/[id]`

#### Path Parameters

| Name                                 | Type   | Description                 |
| ------------------------------------ | ------ | --------------------------- |
| id<mark style="color:red;">\*</mark> | String | ID of the off-chain invoice |

{% tabs %}
{% tab title="201: Created Request created successfully" %}
```json
{
    "id": "63f2f5a7f00a45f276585b28",
    "paymentCurrency": "USDC-matic",
    "buyerInfo": {
        "taxRegistration": "985-80-3313",
        "lastName": "Walton",
        "firstName": "Justin",
        "email": "justin.walton@acme-wholesaler.com",
        "businessName": "Acme Wholesaler Ltd.",
        "address": {
            "streetAddress": "4933 Oakwood Avenue",
            "extendedAddress": "",
            "city": "New York",
            "postalCode": "10038",
            "region": "New York",
            "country": "US",
            "locality": "New York",
            "country-name": "US",
            "extended-address": "",
            "postal-code": "10038",
            "street-address": "4933 Oakwood Avenue"
        },
        "userId": "63c8d2c230d75e750fb449ea"
    },
    "paymentAddress": "0x4886E85E192cdBC81d42D89256a81dAb990CDD74",
    "invoiceItems": [
        {
            "currency": "USD",
            "name": "Television",
            "quantity": 2,
            "tax": {
                "type": "percentage",
                "amount": "20"
            },
            "unitPrice": "9999"
        }
    ],
    "paymentTerms": {
        "dueDate": "2023-01-21T23:59:59.999Z"
    },
    "invoiceNumber": "3",
    "creationDate": "2022-12-22T14:38:16.916Z",
    "meta": {
        "format": "rnf_invoice",
        "version": "0.0.3"
    },
    "sellerInfo": {
        "email": "joe.bloggs@acme-seller.com",
        "address": {
            "streetAddress": "4933 Oakwood Avenue",
            "extendedAddress": "",
            "city": "New York",
            "postalCode": "10038",
            "region": "New York",
            "country": "US",
            "locality": "New York",
            "country-name": "US",
            "extended-address": "",
            "postal-code": "10038",
            "street-address": "4933 Oakwood Avenue"
        },
        "businessName": "Acme Corporation",
        "firstName": "Joe",
        "lastName": "Bloggs",
        "taxRegistration": "123456789",
        "userId": "63995f77f46a063ba7ac34de"
    },
    "createdBy": "63995f77f46a063ba7ac34de",
    "paymentOptions": [
        {
            "type": "wallet",
            "value": {
                "currencies": [
                    "USDC-matic"
                ],
                "paymentInformation": {
                    "paymentAddress": "0x4886E85E192cdBC81d42D89256a81dAb990CDD74",
                    "chain": "matic"
                }
            }
        }
    ],
    "type": "live",
    "trackedTransactions": [],
    "requestId": "017f7f0b5518c6b3c3711b2f5b4517af10195b0f91dc802c3db36f5bf119595fda",
    "invoiceLinks": {
        "pay": "https://app.request.finance/017f7f0b5518c6b3c3711b2f5b4517af10195b0f91dc802c3db36f5bf119595fda?token=0x68d6728d52aadb034938d908d8adb93bb12e64e8982c40b4af275c260b3aee97&enablePayment=true",
        "view": "https://app.request.finance/017f7f0b5518c6b3c3711b2f5b4517af10195b0f91dc802c3db36f5bf119595fda?token=0x68d6728d52aadb034938d908d8adb93bb12e64e8982c40b4af275c260b3aee97",
        "signUpAndPay": "https://app.request.finance/signup?invoice=017f7f0b5518c6b3c3711b2f5b4517af10195b0f91dc802c3db36f5bf119595fda&token=0x68d6728d52aadb034938d908d8adb93bb12e64e8982c40b4af275c260b3aee97&enablePayment=true"
    },
    "role": "seller",
    "tags": [
        "my_tag"
    ]
}
```
{% endtab %}
{% endtabs %}

In the JSON response, you will get a `requestId` field. This is the ID of the newly created request. Please save it in your database, as you will need it to be informed of when the request has been paid. You may use this value in place of the `invoiceId` for future HTTP requests.

## Sharing your Invoice and Getting Paid

To get paid by your customer, you need to redirect them to a payment page hosted by Request Finance. You can get the links to the payment page from the response after creating an on-chain request and embed them in your application or an email.

Using the `invoiceLinks.signUpAndPay` link, you can redirect your customers to a page that looks like the one below, where they can pay your invoice or sign into their Request Finance account, if they have one.

When your customers pay through this page using Request Finance, they can enjoy the convenience and security of our platform, which includes measures to prevent accidental double payments. Additionally, this payment method ensures that the invoice status is automatically updated, simplifying invoice tracking for both you and your customers.

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption><p>Sign up &#x26; pay page</p></figcaption></figure>

## Fetching an Invoice

To check the status of an invoice and understand if it has been paid, please poll the endpoint below regularly. Replace `[id]` with the `requestId` of the Request (recommended), or the `invoiceId`.

## Fetch an invoice by its ID

<mark style="color:blue;">`GET`</mark> `https://api.request.finance/invoices/[id]`

#### Path Parameters

| Name                                 | Type   | Description                  |
| ------------------------------------ | ------ | ---------------------------- |
| id<mark style="color:red;">\*</mark> | String | ID of the request or invoice |

#### Query Parameters

| Name           | Type   | Description                                                                                                                                                                                                          |
| -------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| withLinks=true | String | Includes "Share" and "Payment links" in the response. See [https://docs.request.finance/invoices#sharing-your-invoice-and-getting-paid](https://docs.request.finance/invoices#sharing-your-invoice-and-getting-paid) |

{% tabs %}
{% tab title="200: OK " %}
```json
{
    "id": "63f2f5a7f00a45f276585b28",
    "paymentCurrency": "USDC-matic",
    "buyerInfo": {
        "taxRegistration": "985-80-3313",
        "lastName": "Walton",
        "firstName": "Justin",
        "email": "justin.walton@acme-wholesaler.com",
        "businessName": "Acme Wholesaler Ltd.",
        "address": {
            "streetAddress": "4933 Oakwood Avenue",
            "extendedAddress": "",
            "city": "New York",
            "postalCode": "10038",
            "region": "New York",
            "country": "US",
            "locality": "New York",
            "country-name": "US",
            "extended-address": "",
            "postal-code": "10038",
            "street-address": "4933 Oakwood Avenue"
        },
        "userId": "63c8d2c230d75e750fb449ea"
    },
    "paymentAddress": "0x4886E85E192cdBC81d42D89256a81dAb990CDD74",
    "invoiceItems": [
        {
            "currency": "USD",
            "name": "Television",
            "quantity": 2,
            "tax": {
                "type": "percentage",
                "amount": "20"
            },
            "unitPrice": "9999"
        }
    ],
    "paymentTerms": {
        "dueDate": "2023-01-21T23:59:59.999Z"
    },
    "invoiceNumber": "3",
    "creationDate": "2022-12-22T14:38:16.916Z",
    "meta": {
        "format": "rnf_invoice",
        "version": "0.0.3"
    },
    "sellerInfo": {
        "email": "joe.bloggs@acme-seller.com",
        "address": {
            "streetAddress": "4933 Oakwood Avenue",
            "extendedAddress": "",
            "city": "New York",
            "postalCode": "10038",
            "region": "New York",
            "country": "US",
            "locality": "New York",
            "country-name": "US",
            "extended-address": "",
            "postal-code": "10038",
            "street-address": "4933 Oakwood Avenue"
        },
        "businessName": "Acme Corporation",
        "firstName": "Joe",
        "lastName": "Bloggs",
        "taxRegistration": "123456789",
        "userId": "63995f77f46a063ba7ac34de"
    },
    "createdBy": "63995f77f46a063ba7ac34de",
    "paymentOptions": [
        {
            "type": "wallet",
            "value": {
                "currencies": [
                    "USDC-matic"
                ],
                "paymentInformation": {
                    "paymentAddress": "0x4886E85E192cdBC81d42D89256a81dAb990CDD74",
                    "chain": "matic"
                }
            }
        }
    ],
    "type": "live",
    "requestId": "017f7f0b5518c6b3c3711b2f5b4517af10195b0f91dc802c3db36f5bf119595fda",
    "status": "open",
    "paymentMetadata": {},
    "events": [
        {
            "name": "create",
            "userId": "63995f77f46a063ba7ac34de",
            "date": "2023-02-20T04:28:12.000Z"
        }
    ],
    "trackedTransactions": [],
    "role": "seller",
    "tags": [
        "my_tag"
    ]
}
```
{% endtab %}
{% endtabs %}

You can check the `status` field of the JSON response. The different statuses of an invoice are the following:

* `open` – The request associated with the invoice has been created on-chain. The buyer has not yet paid the invoice.
* `accepted` – The invoice has been approved by the buyer.
* `declaredPaid` – The buyer declared the invoice as paid. The seller has to confirm before the invoice can move into the paid status. This is necessary for currencies, where the Request Network does not yet support payment detection.
* `paid` – Final state. The buyer paid the invoice.
* `canceled` – Final state. The seller canceled the invoice.
* `rejected` – Final state. The buyer rejected the invoice.
* `scheduled` – Status for recurring invoices. Indicates that an invoice will be created on a specific date in the future.
* `draft` – The invoice is in draft status. It can still be edited and was not yet converted into an on-chain request. This status is currently only supported when creating an invoice in the Request Finance UI.

When creating an on-chain request with the previously described process, you should end up with a pending status while the request is being persisted on-chain (this process is asynchronous), followed by an `open` status once the request is actually created.

You can use the value `paid` to classify the Request as "fulfilled" and stop polling for a new status.

When the value matches `rejected` or `canceled` you can also stop polling: it means that the request has been manually canceled out by the payer or the payee respectively, and thus will not get paid.

## Listing Invoices

Fetch a list of the user's invoices. Use the `creationDateRange` parameter to filter for invoices created in a date range. Other filters are listed below for your convenience. For example, the `search=tx_hash` filter is a valuable filter to use when presenting the user with a list of invoices associated with a transaction hash.

## List invoices

<mark style="color:blue;">`GET`</mark> `https://api.request.finance/invoices`

#### Query Parameters

| Name              | Type      | Description                                                                                                                                                                                                                               |
| ----------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| take              | Integer   | How many items should be returned per page. Default: `25`. Maximum: `100`.                                                                                                                                                                |
| skip              | Integer   | Use this filter to paginate the results (= skip to a certain page number). Default: `0`.                                                                                                                                                  |
| search            | String    | Filter by transaction hash, invoice number, company, and other fields. Example: `&search=0xef...`                                                                                                                                         |
| status            | String\[] | Filter by invoice status. Available statuses are: `draft`, `pending`, `open`, `paid`, `declaredPaid`, `accepted`, `canceled`, `rejected`, `scheduled`, `overdue`. Example: `&status[]=draft`                                              |
| creationDateRange | String    | <p>Filter by creation date (ISO 8601 format).<br>Example: <code>&#x26;creationDateRange={"from":"2022-06-24T00:00:00.000Z","to":"2022-08-22T00:00:00.000Z"}</code></p>                                                                    |
| variant           | String    | Filter by invoice format. Use `rnf_invoice` to filter for invoices and `rnf_salary` to filter for salaries.                                                                                                                               |
| filterBy          | String    | This filter accepts two values: `sent` or `received` ; returning only invoices sent or received by the user.                                                                                                                              |
| withLinks         | Boolean   | Include the "Share" and "Payment links" in the response. Default: `false`. See [https://docs.request.finance/invoices#sharing-your-invoice-and-getting-paid](https://docs.request.finance/invoices#sharing-your-invoice-and-getting-paid) |
| format            | String    | You can set the query parameter`&format=paginated` which will return additional information like the total number of results with and without filters, as well as the number of results per invoice status.                               |

{% tabs %}
{% tab title="200: OK " %}
```json
[
    {
        "id": "63f3081d8c008a5de554ca97",
        "paymentCurrency": "USDC-matic",
        "buyerInfo": {
            "taxRegistration": "985-80-3313",
            "lastName": "Walton",
            "firstName": "Justin",
            "email": "justin.walton@acme-wholesaler.com",
            "businessName": "Acme Wholesaler Ltd.",
            "address": {
                "streetAddress": "4933 Oakwood Avenue",
                "extendedAddress": "",
                "city": "New York",
                "postalCode": "10038",
                "region": "New York",
                "country": "US",
                "locality": "New York",
                "country-name": "US",
                "extended-address": "",
                "postal-code": "10038",
                "street-address": "4933 Oakwood Avenue"
            },
            "userId": "63c8d2c230d75e750fb449ea"
        },
        "paymentAddress": "0x4886E85E192cdBC81d42D89256a81dAb990CDD74",
        "invoiceItems": [
            {
                "currency": "USD",
                "name": "TV Stand",
                "quantity": 1,
                "tax": {
                    "type": "percentage",
                    "amount": "20"
                },
                "unitPrice": "2000"
            }
        ],
        "paymentTerms": {
            "dueDate": "2023-01-21T23:59:59.999Z"
        },
        "invoiceNumber": "4",
        "creationDate": "2022-12-22T14:38:16.916Z",
        "meta": {
            "format": "rnf_invoice",
            "version": "0.0.3"
        },
        "sellerInfo": {
            "email": "joe.bloggs@acme-seller.com",
            "address": {
                "streetAddress": "4933 Oakwood Avenue",
                "extendedAddress": "",
                "city": "New York",
                "postalCode": "10038",
                "region": "New York",
                "country": "US",
                "locality": "New York",
                "country-name": "US",
                "extended-address": "",
                "postal-code": "10038",
                "street-address": "4933 Oakwood Avenue"
            },
            "businessName": "Acme Corporation",
            "firstName": "Joe",
            "lastName": "Bloggs",
            "taxRegistration": "123456789",
            "userId": "63995f77f46a063ba7ac34de"
        },
        "createdBy": "63995f77f46a063ba7ac34de",
        "paymentOptions": [
            {
                "type": "wallet",
                "value": {
                    "currencies": [
                        "USDC-matic"
                    ],
                    "paymentInformation": {
                        "paymentAddress": "0x4886E85E192cdBC81d42D89256a81dAb990CDD74",
                        "chain": "matic"
                    }
                }
            }
        ],
        "type": "live",
        "requestId": "01cb820a384b1e2c4d746a7e6080530f558bb25a211f1e8e7724ea2b6f9fc2789a",
        "status": "open",
        "role": "seller",
        "tags": [
            "my_tag"
        ],
        "trackedTransactions": []
    },
    {
        "id": "63f2f5a7f00a45f276585b28",
        "paymentCurrency": "USDC-matic",
        "buyerInfo": {
            "taxRegistration": "985-80-3313",
            "lastName": "Walton",
            "firstName": "Justin",
            "email": "justin.walton@acme-wholesaler.com",
            "businessName": "Acme Wholesaler Ltd.",
            "address": {
                "streetAddress": "4933 Oakwood Avenue",
                "extendedAddress": "",
                "city": "New York",
                "postalCode": "10038",
                "region": "New York",
                "country": "US",
                "locality": "New York",
                "country-name": "US",
                "extended-address": "",
                "postal-code": "10038",
                "street-address": "4933 Oakwood Avenue"
            },
            "userId": "63c8d2c230d75e750fb449ea"
        },
        "paymentAddress": "0x4886E85E192cdBC81d42D89256a81dAb990CDD74",
        "invoiceItems": [
            {
                "currency": "USD",
                "name": "Television",
                "quantity": 2,
                "tax": {
                    "type": "percentage",
                    "amount": "20"
                },
                "unitPrice": "9999"
            }
        ],
        "paymentTerms": {
            "dueDate": "2023-01-21T23:59:59.999Z"
        },
        "invoiceNumber": "3",
        "creationDate": "2022-12-22T14:38:16.916Z",
        "meta": {
            "format": "rnf_invoice",
            "version": "0.0.3"
        },
        "sellerInfo": {
            "email": "joe.bloggs@acme-seller.com",
            "address": {
                "streetAddress": "4933 Oakwood Avenue",
                "extendedAddress": "",
                "city": "New York",
                "postalCode": "10038",
                "region": "New York",
                "country": "US",
                "locality": "New York",
                "country-name": "US",
                "extended-address": "",
                "postal-code": "10038",
                "street-address": "4933 Oakwood Avenue"
            },
            "businessName": "Acme Corporation",
            "firstName": "Joe",
            "lastName": "Bloggs",
            "taxRegistration": "123456789",
            "userId": "63995f77f46a063ba7ac34de"
        },
        "createdBy": "63995f77f46a063ba7ac34de",
        "paymentOptions": [
            {
                "type": "wallet",
                "value": {
                    "currencies": [
                        "USDC-matic"
                    ],
                    "paymentInformation": {
                        "paymentAddress": "0x4886E85E192cdBC81d42D89256a81dAb990CDD74",
                        "chain": "matic"
                    }
                }
            }
        ],
        "type": "live",
        "requestId": "017f7f0b5518c6b3c3711b2f5b4517af10195b0f91dc802c3db36f5bf119595fda",
        "status": "open",
        "paymentMetadata": {},
        "events": [
            {
                "name": "create",
                "userId": "63995f77f46a063ba7ac34de",
                "date": "2023-02-20T04:28:12.000Z"
            }
        ],
        "role": "seller",
        "tags": [
            "my_tag"
        ],
        "trackedTransactions": []
    }
]
```
{% endtab %}
{% endtabs %}

## Approving/Rejecting/Canceling an Invoice

**Approving**:

* _As a buyer_, if you received an invoice from one of your supplier/contractors, you can approve it prior to paying. Approved invoices will show up in the ["Approved" tab of the "Pay" menu](https://app.request.finance/pay/bills?f=approved) in the Request Finance app and indicate that the invoice has been accepted by you and is ready for payment.\
  Only `open` invoices can be approved.
* _As a seller_, you cannot approve an invoice. Once a buyer approves your invoice, it will show up in the ["Approved" tab of the "Get paid" menu](https://app.request.finance/get-paid/sent?f=approved).

**Rejecting**

* _As a buyer_, if you received an incorrect invoice from one of your supplier/contractors, you can reject it. Rejected invoices will show up in the ["Rejected" tab of the "Pay" menu](https://app.request.finance/pay/bills?f=rejected) in the Request Finance app and indicate that the invoice has been rejected by you and won't be paid.\
  Only `open` and `accepted` invoices can be rejected.
* _As a seller_, you cannot reject an invoice. Once a buyer rejects your invoice, it will show up in the ["Rejected" tab of the "Get paid" menu](https://app.request.finance/get-paid/sent?f=rejected).

**Canceling**:

* _As a seller_, if you issued an invoice to your client but realised a mistake, you can cancel it. Canceled invoices will show in the ["Voided" tab of the "Get paid" menu](https://app.request.finance/get-paid/sent?f=voided).\
  Only `open` and `accepted` invoices can be canceled.
* _As a buyer_, you cannot cancel an invoice. Once a seller cancels an invoice, it will show up in the ["Voided" tab of the "Pay" menu](https://app.request.finance/pay/bills?f=voided).

## Approve, reject or cancel an invoice

<mark style="color:green;">`POST`</mark> `https://api.request.finance/invoices/[id]/changes`

#### Path Parameters

| Name                                 | Type   | Description       |
| ------------------------------------ | ------ | ----------------- |
| id<mark style="color:red;">\*</mark> | String | ID of the invoice |

#### Request Body

| Name                                         | Type   | Description                                                                                                                                                                               |
| -------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| type<mark style="color:red;">\*</mark>       | String | <p>The type of change. Use<br>"<code>accept</code>" to approve an invoice<br>"<code>reject</code>" to reject<br>"<code>cancel</code>" to cancel</p>                                       |
| input.note<mark style="color:red;">\*</mark> | String | <p>Required when rejecting an invoice. Include a rejection reason.<br><br>Example:<br><br><code>"input":</code><br><code>{</code><br><code>note: "Duplicate"</code><br><code>}</code></p> |

{% tabs %}
{% tab title="200: OK Example response when canceling" %}
```json
{
    "id": "646d68bdf64d4a4839eafe25",
    "requestId": "0196124706be086a302dfdff2831270120fdc2f5efc5bcf12e48e19082c68fe23c",
    "actionType": "cancel",
    "input": {},
    "networkType": "test",
    "chainName": "goerli",
    "userId": "63f459c11727622c09b2932a",
    "timestamp": "2023-05-24T01:30:37.811Z",
    "status": "pending",
    "sendNotification": false
}
```
{% endtab %}
{% endtabs %}
