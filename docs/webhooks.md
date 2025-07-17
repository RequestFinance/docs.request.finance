---
description: Request Finance API - Webhooks Documentation
---

# Webhooks

## Introduction

Webhooks in Request Finance allow you to receive real-time notifications about changes to invoices, such as when they are created, accepted, canceled, rejected, or paid. This guide explains how to set up and secure webhooks for your integration with the Request Finance API.

## Prerequisites

1. **Create an OAuth app:** See [#authentication](going-live.md#authentication "mention")
2. **Whitelist Your Account**: Before you can use webhooks, you need to be whitelisted for the feature. Contact Request Finance support to request access.

## Setting Up Webhooks

### Step 1: Add Webhook URL and Secret

Once your account is whitelisted, follow these steps to add your webhook URL and secret:

1. Navigate to the `Settings > Developer > Apps` page in the Request Finance dashboard.
2. Create or edit your OAuth application.
3. Enter your webhook URL.
4. Enter your webhook secret. This secret is used to verify the integrity of the incoming requests.

The webhook URL and secret are mandatory for events to be sent to your URL.

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption><p>Edit your OAuth app, and add the webhook URL and secret</p></figcaption></figure>

### Step 2: Verify Webhook Setup

To ensure that your webhooks are working correctly, you can use testing services like [Webhook.site](https://webhook.site) or [Webhook Test](https://webhook-test.com/). These services allow you to inspect the incoming webhook requests and verify their format.

## Webhook Events

When an event occurs, Request Finance will send a JSON payload to your webhook URL. The payload format is as follows:

```json
{
  "variant": "rnf_invoice", // Other possible values: rnf_salary
  "event": "create", // Other possible values: accept, cancel, reject, paid
  "timestamp": 1720605600000, // Unix timestamp in milliseconds
  "invoice": {
    ...
  }
}
```

The `invoice` object is similar to the one received by the `GET /invoices/:id` API, see [#fetch-an-invoice-by-its-id](invoices.md#fetch-an-invoice-by-its-id "mention").

### Event Sources

Depending on the usage of your OAuth application, you will receive events for different types of invoices:

* If your OAuth application is not yet used for interracting with the Request Finance API, you will still receive webhook events for every invoice sent or received by your account or organization.
* If your OAuth application follows the [Authorization Code Flow](https://auth0.com/docs/get-started/authentication-and-authorization-flow/authorization-code-flow) and is used to read users' data, you will receive webhook events for every invoice sent or received by users who have authorized your application.
* If your OAuth application follows the [Client Credentials Flow](https://auth0.com/docs/get-started/authentication-and-authorization-flow/client-credentials-flow) and sends invoices, you will receive webhook events for every invoice it creates.

### Event Types

The `event` field can have the following values:

* `create`: When an invoice is created.
* `accept`: When an invoice is accepted (by the buyer).
* `cancel`: When an invoice is canceled (by the seller).
* `reject`: When an invoice is rejected (by the buyer).
* `paid`: When an invoice is paid.

## Securing Your Webhooks

To ensure that the webhook requests are legitimate and not coming from unauthorized sources, you should verify the `X-Webhook-Signature` HTTP header sent with each event. This header contains the SHA256 signature of the request body, generated using your webhook secret.

### Verification Example in Node.js

Here's an example of how to verify the webhook signature in Node.js:

```javascript
const crypto = require('crypto');

// Your webhook secret
const secret = 'your_webhook_secret';

// The raw body of the webhook event (as a string)
const body = '{"variant":"rnf_invoice","event":"create","timestamp":"2024-07-10T10:00:00Z","invoice":{...}}';

// The signature from the X-Webhook-Signature header
const signature = req.headers['x-webhook-signature'];

// Create the HMAC
const hmac = crypto.createHmac('sha256', secret);
hmac.update(body);
const digest = hmac.digest('hex');

// Compare the generated HMAC digest with the signature
if (digest === signature) {
  console.log('Webhook signature is valid.');
} else {
  console.log('Invalid webhook signature.');
}
```
