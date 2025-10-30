---
description: Only used when developing in Sandbox
---

# Sandbox Special Moves

When developing on the staging server, you can ping these endpoints to simulate a KYB/C check passing or a Payment Detail being approved.

## Update the status of a User's KYC application

Note: only the status attribute can be updated to one of the values listed [here](../api-reference/kyc-sessions/). If you want to clear the User, set `status` to `approved`.

```json
curl https://{{base_url}}/sandbox/users/:user_id/kycs
-X PATCH \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json"
-d '{
    "kyc": {
        "status": "approved"
    }
}'
```

## Update the status of a Payment Detail

Note: only the status attribute can be updated to one of the values listed [here](../api-reference/kyc-sessions/). If you flip the status to `approved` any pending Outstanding Actions associated with the Payment Detail will be marked and verified as complete.

```json
curl https://{{base_url}}/sandbox/users/:user_id/payment_details/:payment_detail_id
-X PATCH \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json"
-d '{
    "payment_detail": {
        "status": "approved"
    }
}'
```

## Simulate Webhooks

Sometimes you want to test webhook handling without having to perform the actions necessary to trigger a webhook firing. This endpoint will return a payload in response to your request, but will then also send an asynchronous response to your defined callback URL. You can use this endpoint to trigger web-hooks with a variety of statuses to test how your integration will handle them.\
\
To test against specific objects you can also send a UUID for `offramp_id`, `onramp_id`, `user_id` or `payment_detail_id`. The payload we return will reflect the specified UUID for that attribute.

```json
curl https://{{base_url}}/sandbox/webhook?webhook_type=WEBHOOK_TYPE&status=STATUS&user_id=USER_ID&payment_detail_id=PAYMENT_DETAIL_ID&offramp_id=OFFRAMP_ID
-X GET \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json"
```



#### Webhook Type

| Possible values for webhook\_type | Possible values for statuses                                                                                                                                                                                                                                                                                                                                                                                       |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| kyc                               | <p><code>"not_started", "initiated", "pending_assessment", "application_queued", "awaiting_manual_review", "retry_required", "retry_denied", "approved", "failed", "full_clearance"</code><br><br><code>NB: approved KYC will not have all the rails immediately cleared. This is similar to productione, where some currencies/rails require additional checks. Full clearance will approve all rails.</code></p> |
| payment\_detail                   | `"initiated", "approved", "pending", "failed"`                                                                                                                                                                                                                                                                                                                                                                     |
| offramp                           | `"initiated", "pending_internal_assessment", "sending_fiat", "ongoing_checks", "fiat_sent", "bounced", "failed"`                                                                                                                                                                                                                                                                                                   |
| onramp                            | `"initiated", "sending_fiat", "crypto_sent", "failed"`                                                                                                                                                                                                                                                                                                                                                             |

#### Query Parmas

<table><thead><tr><th width="198">Query param</th><th width="99">Required</th><th>Description</th></tr></thead><tbody><tr><td>webhook_type</td><td>true</td><td>The webhook you want to simulate</td></tr><tr><td>status</td><td>true</td><td>The status you want to simulate</td></tr><tr><td>user_id</td><td>false</td><td>User ID</td></tr><tr><td>payment_detail_id</td><td>false</td><td>Payment Detail ID</td></tr><tr><td>quote_id</td><td>false</td><td>Quote ID</td></tr><tr><td>offramp_id</td><td>false</td><td>Offramp ID</td></tr><tr><td>onramp_id</td><td>false</td><td>Onramp ID</td></tr><tr><td>sepa_disabled</td><td>false</td><td>Can be used to test a kyc edge case, where a user is cleared for all rails apart from sepa. Value must be a boolean.</td></tr></tbody></table>

## Using the Goerli/Sepolia network

When executing a quote in the the `staging` environment, you can specify your Crypto Transfer to have a `blockchain` value of `ethereum` and a`network`value of `goerli/sepolia.`

With these values submitted, you can also submit a `tx_id` of a transaction on the Goerli/Sepolia network for validation.
