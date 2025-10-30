---
description: How to verify webhooks indeed come from Request Technology.
---

# Webhook Signatures

1. On request we can generate a secret to be shared between us and your organisation which will be used to sign/verify.
2. We will use this shared secret to sign a string which will be sent in a header entitled X-Sig. This includes a timestamp(t) and a signature(s).
3.  Example:

    { X-Sig: "t=1688740624, s=a66ca938781fe643f7432a55ee3f674de9e28b95db7a90999418b45a65c24c21"}
4. In order to generate this signature, Request Technologies akes a string as follows: "{timestamp}.{json\_request\_body}". We then sign this with the shared secret using the sha256 algorithm. This returns a hex-encoded string.
5. In order to verify the webhook you will need to first get the X-sig header and split out the t(timestamp) and s(sig) values.
6. Using the t (timestamp) value and the body of the incoming request (json string) you can then build the signed string as follows: "{t}.{json\_body}".
7. Using the shared secret and the sha256 algorithm generate a signature and compare this against the signature (s) value you stripped from the X-Sig header.
8.  Example generation of signature (Ruby).



    ```ruby
    OpenSSL::HMAC.hexdigest(OpenSSL::Digest.new('sha256'), ENV['REQUEST_WEBHOOK_SECRET_KEY'], "#{t}.#{json_body}")
    ```
