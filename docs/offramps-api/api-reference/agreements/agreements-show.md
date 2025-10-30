---
description: Show the terms and conditions flow
---

# Agreements#Show

**Render the following URL in an iFrame**

```json
https://{{base_url}}/public/agreements?email={encodeURIComponent(USER_EMAIL)}
```

Each time a user completes an agreement, we'll send an event containing information about the agreement they signed, like { agreements: agreed\_payso }. Additionally, once the entire flow is completed, we'll emit a { agreements: complete } event. You can easily listen for these events using the following JavaScript code in your frontend.

Below is an example of how you might implement the Agreement flow in your front-end. In this example we are using React, but ChatGPT can transpile this to your preferred language if you ask it nicely.

{% hint style="warning" %}
Make sure to encode the email of termsUrl with **encodeURIComponent**().
{% endhint %}

```javascript
import React, { useRef }  from 'react';

const Agreements = ({ onComplete }) => {
  const iframeRef = useRef();
  const termsUrl = 'https://{{base_url}}/public/agreements?email={encodeURIComponent(USER_EMAIL)}'

  // Set up a listener for the event that is fired when the user signs the Agreement
  useEffect(() => {
    window.addEventListener("message", onCompleteHandler);
    return () => {
      window.removeEventListener("message", onCompleteHandler);
    };
  }, []);

  // Do something in your UI when the event fires
  const onCompleteHandler = (event) => {
    if (event.data.agreements === 'complete') {
      onComplete();
    } else if (Object.keys(event.data.agreements).find(i =>i.includes("agreed"))) {
      // When a user has signed an agreement, refresh the termsUrl.
      // This improves cross-browser support and prevents caching issues.
      iframeRef.current.src = termsUrl
    }
  }

  // Render the Agreement, passing in the User's email as a query parameter
  return <iframe ref={iframeRef} src={termsUrl} />
}

export default Agreements;
```

Once the flow has been completed, you can then [create a User object](../users/users-create.md) with the same email that was used to sign the Agreement.

{% hint style="danger" %}
If a User is created with a different email, or did not complete the flow, then it's likely they won't be cleared to use the service.
{% endhint %}
