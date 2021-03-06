# RM - Open API

Revenue Monster (hereafter mentioned as RM) Open APIs allow developers to manage payments, users, stores, loyalty, and social media through RESTful API or SDK. All RM products have API for most of its core functionalities. Start with our comprehensive API to reimagine your business.

**API Environment Summary** <br />

There are two services for our API (OAuth and Open API),both for sandbox and production environment. OAuth server is for authentication, Open API server is for core functions. You may test with sandbox endpoints before going production. You could self-signup for sandbox access and contact <sandbox@revenuemonster.my> to activate your sandbox account.

<strong>Sandbox Environment: -</strong>
<br /><https://sb-oauth.revenuemonster.my><br /> <https://sb-open.revenuemonster.my>

<strong>Production Environment: -</strong>
<br /><https://oauth.revenuemonster.my><br /> <https://open.revenuemonster.my>

**Before You Start**

Go to our merchant portal in Production [Merchant Portal](https://merchant.revenuemonster.my/) or [Sandbox Merchant Portal](https://sb-merchant.revenuemonster.my/) to sign up as merchant.

Submit all required documents as shown in our merchant portal and get approval from our admin. Should you need more assistance, please contact us at <bd@revenuemonster.my>.

Kindly go through `Signature Algorithm` to see our signing mechanism before proceed to call payment API endpoint(s). Payment API have higher security requirements than the rest.

##Scenario / Business Use Case

For Merchant that using RM API to intergrate their E-Commerce platform :-

Web Payment
Mobile Payment
Mobile Browser

For Merchant that using Shop / Cafe :-

Transaction QR

- Redirect URL (URL to redirect after payment is made)
- Notify URL (This is a notify URL or callback URL to inform server on transaction status after payment made.)

QuickPay

Intergrate for Vending Machine :-

Transaction QR

Intergrate Supermarket

QuickPay
( To make payments with Quick Pay. Merchant to scan user's wallet.

- Scope: manage_payment
- Authentication: Access token obtained from Generate Access Token into Authorization header value as Bearer [access_token].
- If merchant has not entered Webhook URL and/or Client Public Key in Merchant Portal, system will throw error as below: )
