#Quick Start & SDK

\*Note: The following steps document the RESTful API. For language specific SDK(s), please refer to the [SDK section](https://doc.revenuemonster.my/#sdk-beta). need to change URL

- <strong>Step 1: Create Developer Application</strong>

[Create a developer application](https://doc.revenuemonster.my/#create-developer-application) in RM merchant portal for your developer project. The application settings help you to manage API credentials, provide callback endpoints and with debugging utilties.

- <strong>Step 2: Authentication</strong>

Once you have your API credentials, follow our [Authentication](https://doc.revenuemonster.my/#create-developer-application) process to exchange access token and refresh token for subsequent API calls.

- <strong>Step 3: Signature (Payment endpoints only)</strong>

Payment operations require higher security with [Signature](https://doc.revenuemonster.my/#signature-algorithm), all payment endpoints require the requests to be signed.

- <strong>Step 4: Call API</strong>

Use access token to call RESTful API endpoints. (Signature is optional for non-payment endpoints.)
