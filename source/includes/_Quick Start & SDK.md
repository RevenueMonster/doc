#Quick Start & SDK

\*Note: The following steps document the RESTful API. For language specific SDK(s), please refer to the [SDK section](https://doc.revenuemonster.my/#0f854ba3-9051-4747-83d7-c532392e07f0). need to change URL

-<strong>Step 1: Create Developer Application</strong>

[Create a developer application](https://doc.revenuemonster.my/#c68f6785-4ee4-4088-8f60-dc49a695611f) <!---need to change URL--->
in RM merchant portal for your developer project. The application settings help you to manage API credentials, provide callback endpoints and with debugging utilties.

-<strong>Step 2: Authentication</strong>

Once you have your API credentials, follow our [Authentication](https://doc.revenuemonster.my/#create-developer-application) <!--need to change URL--> process to exchange access token and refresh token for subsequent API calls.

-<strong>Step 3: Signature (Payment endpoints only)</strong>

Payment operations require higher security with [Signature](https://doc.revenuemonster.my/#signature-algorithm), <!-- need to change URL --> all payment endpoints require the requests to be signed.

-<strong>Step 4: Call API</strong>

Use access token to call RESTful API endpoints. (Signature is optional for non-payment endpoints.)
