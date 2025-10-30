---
description: >-
  Some processes - namely KYC and Offramps - may take a few hours to progress.
  You can receive updates about their progression via our Webhooks service.
---

# Webhooks

### Retries

In the event that your server fails to respond to a webhook with a 200 status code, our system will initiate automatic retry attempts. \
\
A total of 5 retry attempts will be made before we cease sending further webhooks. The timing of these retry attempts is outlined below.

| Retry Count | Retry Time |
| ----------- | ---------- |
| 0           | 0:00:00    |
| 1           | 0:00:16    |
| 2           | 0:00:47    |
| 3           | 0:02:23    |
| 4           | 0:06:54    |
| 5           | 0:17:34    |

&#x20;
