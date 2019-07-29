#Payment-Transaction QR

Scenarios:

1. Wechat Official Account (OA) Payment
2. Website QR Code online payment. Example, E-commerce website shows QR Code with an amount for user to scan with their Mobile wallet.
3. Vending Machines / Sales Kiosk

To make payment when user scan merchant's displayed QR code with mobile wallet.

- Scope: `manage_payment`
- Authentication: Access token obtained from [Generate Access Token](https://doc.revenuemonster.my/#66368026-71ee-4640-8ad7-208f843c6d6c) into `Authorization` header value as `Bearer [access_token]`.

**Illustration of transaction QR Code**

1. Get QR Code URL `qrCodeUrl` from the endpoint below and generate QR Code as below.
   Example of QR Code URL: https://dev-rm-api.ap.ngrok.io/payment/unified?code=a669adc3b06fe5cef977cc762f40ce8c <br>

2. If `"isPreFillAmount": false`, then user will be prompted to key-in amount for payment, followed by Step 3. <br>
   ![No Prefill Amount](https://storage.googleapis.com/rm-portal-assets/img/rm-doc/transaction-qr/1.jpeg)

3. If `"isPreFillAmount": true`, then user will be directly prompted for payment. <br>
   ![Prompt Payment](https://storage.googleapis.com/rm-portal-assets/img/rm-doc/transaction-qr/2.jpeg)

4. Key in payment pin to complete payment. <br>
   ![Complete Payment](https://storage.googleapis.com/rm-portal-assets/img/rm-doc/transaction-qr/3.jpeg)

5. User will get payment status notification. <br>
   ![Successful Payment](https://storage.googleapis.com/rm-portal-assets/img/rm-doc/transaction-qr/4.jpeg)

6. User will be redirected to `redirectUrl` specified during QR code creation. <br>

7. User will also get this notification in Service Notification. <br>
   ![Notification](https://storage.googleapis.com/rm-portal-assets/img/rm-doc/transaction-qr/5.jpeg)
   ![Payment Details](https://storage.googleapis.com/rm-portal-assets/img/rm-doc/transaction-qr/7.jpeg)

8. Merchant can view the transaction record in Merchant Portal. <br>
   ![Merchant Transaction Record](https://storage.googleapis.com/rm-portal-assets/img/rm-doc/transaction-qr/6.png)

<!---=================================--->
<!---Create Transaction QR Code or URL--->
<!---=================================--->

##Create Transaction QR Code or URL
**Method <span style="color:Orange" , bold >`POST`</span>**

<code>https://sb-open.revenuemonster.my/v3/payment/transaction/qrcode</code>

To create static/dynamic QR code for user scanning merchant's displayed QR.

**_REQUEST_**

<strong>Request Parameters:</strong>

| Parameter                    | Type     | Required | Description                                                                                                                        |                                                   Example                                                    |
| ---------------------------- | -------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------: |
| <code>amount</code>          | Uint     | Yes      | Amount of order in cent. Only required when "isPrefillAmount" = true. (min RM 0.10 or amount: 10)                                  |                                                     100                                                      |
| <code>currencyType</code>    | String   | Yes      | Currency notation (currently only support `MYR`)                                                                                   |                                                    "MYR"                                                     |
| <code>method</code>          | []String | No       | Wallet provider for payment, supports "WECHATPAY", "PRESTO" , "BOOST" , "ALIPAY_CN" , "GRABPAY_MY".                                | ["WECHATPAY","WECHATPAY_MY", <br/> "WECHATPAY_CN","PRESTO_MY",<br/>"BOOST_MY",<br/>"ALIPAY_CN","GRABPAY_MY"] |
| <code>expiry</code>          | Object   | No       | Object of expiry                                                                                                                   |                                         (Refer to explanation below)                                         |
| <code>order</code>           | Object   | Yes      | Object of order                                                                                                                    |                                         (Refer to explanation below)                                         |
| <code>redirectUrl</code>     | String   | No       | URL to redirect after payment is made. Default is "".                                                                              |                                      "https://www.apple.com/my/iphone/"                                      |
| <code>type</code>            | String   | Yes      | "STATIC" (for permanent use) or "DYNAMIC" (for one-time use)                                                                       |                                                   "STATIC"                                                   |
| <code>storeId</code>         | String   | Yes      | ID of the store to create QR code                                                                                                  |                                             "10946114768247530"                                              |
| <code>isPreFillAmount</code> | Bool     | No       | To indicate QR code has pre-fill amount. Default is false. (i.e. Amount will be shown directly on user's wallet without keying-in) |                                                     true                                                     |

> Example Request

```json
curl --location --request POST "https://sb-open.revenuemonster.my/v3/payment/transaction/qrcode" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 pLZz2vnRYHKPUd28gz+f3gIPimH+dHu1xNZqBqlNVQFOdDY1UPpA8S9lIHb4vUhQlEqLS/jJp4zETKA0q4qIlA==" \
  --header "X-Nonce-Str: mpnbwsaizkwaykemxfolmmhvyzvrgnnh" \
  --header "X-Timestamp: 15347569119413" \
  --data "{\"amount\":100,\"currencyType\":\"MYR\",\"expiry\":{\"type\":\"PERMANENT\"},\"isPreFillAmount\":true,\"method\": [\"WECHATPAY\"],\"order\":{\"detail\":\"detail\",\"title\":\"title\"},\"redirectUrl\":\"https://www.baidu.com/\",\"storeId\":\"10946114768247530\",\"type\":\"DYNAMIC\"}"
```

<strong>Expiry object (`"expiry"`):</strong>

| Parameter              | Type     | Required | Description                                                                               | Example                            |
| ---------------------- | -------- | -------- | ----------------------------------------------------------------------------------------- | ---------------------------------- |
| <code>type</code>      | String   | Yes      | "DYNAMIC" (days from now), "FIX" (specific fixed date) or "PERMANENT" (never expire)      | "PERMANENT"                        |
| <code>day</code>       | Uint     | No       | Only required by "DYNAMIC" expiry type. To indicate number of days from now until expiry. | 3                                  |
| <code>expiredAt</code> | DateTime | No       | Only required by "FIXED". To indicate specific expiry date.                               | "2020-10-07T17:44:26.679908+08:00" |

> Example Respond

```json
{
  "item": {
    "store": {
      "id": "10946114768247530",
      "name": "One Utama",
      "addressLine1": "ANYTHING",
      "addressLine2": "",
      "postCode": "48484",
      "city": "KUALA LUMPUR",
      "state": "W.P. KUALA LUMPUR",
      "country": "MALAYSIA",
      "countryCode": "60",
      "phoneNumber": "12312341234",
      "geoLocation": {
        "latitude": 0,
        "longitude": 0
      },
      "status": "ACTIVE",
      "createdAt": "2018-06-03T08:53:48Z",
      "updatedAt": "2018-06-03T08:53:48Z"
    },
    "type": "DYNAMIC",
    "isPreFillAmount": true,
    "currencyType": "MYR",
    "amount": 100,
    "platform": "OPEN_API",
    "method": ["WECHATPAY"],
    "expiry": {
      "type": "PERMANENT",
      "day": 0,
      "expiredAt": "2050-12-31T23:59:59Z"
    },
    "code": "237fff27513b29ddd364e595d6c2eaf2",
    "status": "VALID",
    "qrCodeUrl": "https://sb-api.revenuemonster.my/payment/unified?code=237fff27513b29ddd364e595d6c2eaf2",
    "redirectUrl": "https://www.baidu.com/",
    "order": {
      "title": "title",
      "detail": "detail"
    },
    "createdAt": "2018-08-20T09:27:47.68849666Z",
    "updatedAt": "2018-08-20T09:27:47.688496777Z"
  },
  "code": "SUCCESS"
}
```

<strong>Order object (`"order"`):</strong>

| Parameter                     | Type   | Required | Description                     | Example                                 |
| ----------------------------- | ------ | -------- | ------------------------------- | --------------------------------------- |
| <code>details</code>          | String | Yes      | Order details, max: 600         | "1 x iPhone X; 2 x SAMSUNG S8"          |
| <code>title</code>            | String | Yes      | Order title, max: 32            | "Sales"                                 |
| <code> additionalData </code> | String | Yes      | Order additional data, max: 128 | "Sales for customer xxx at branch xxx." |

**_RESPONSE_**

<strong>Response Parameters:</strong>

| Parameter          | Type   | Description                                                                                               | Example                      |
| ------------------ | ------ | --------------------------------------------------------------------------------------------------------- | ---------------------------- |
| <code>items</code> | Object | Transaction object                                                                                        | (Refer to explanation below) |
| <code>code</code>  | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"                    |

<strong>Transaction object (`"item"`):</strong>

| Parameter                    | Type     | Description                                                                                         | Example                                                                                                      |
| ---------------------------- | -------- | --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| <code>store</code>           | Object   | Store object                                                                                        | (Refer to explanation below)                                                                                 |
| <code>type</code>            | String   | "DYNAMIC" (days from now), "FIXED" (specific fixed date) or "PERMANENT" (never expire)              | "PERMANENT"                                                                                                  |
| <code>isPreFillAmount</code> | Bool     | To indicate QR code has pre-fill amount                                                             | true                                                                                                         |
| <code>currencyType</code>    | String   | Currency notation                                                                                   | "MYR"                                                                                                        |
| <code>amount</code>          | Uint     | Amount of order in cent. Only required when "isPrefillAmount" = true.                               | 100                                                                                                          |
| <code>platform</code>        | String   | Currently only support "OPEN_API"                                                                   | "OPEN_API"                                                                                                   |
| <code>method</code>          | []String | Wallet provider for payment, supports "WECHATPAY", "PRESTO" , "BOOST" , "ALIPAY_CN" , "GRABPAY_MY". | ["WECHATPAY","WECHATPAY_MY", <br/> "WECHATPAY_CN","PRESTO_MY",<br/>"BOOST_MY",<br/>"ALIPAY_CN","GRABPAY_MY"] |
| <code>expiry</code>          | Object   | Object of expiry                                                                                    | (Refer to explanation above)                                                                                 |
| <code>code</code>            | String   | Embedded code in QR                                                                                 | "c8ff3df0605a5f20cd6476661072eade"                                                                           |
| <code>status</code>          | String   | "VALID" (always valid for static QR) or "REDEEMED" (only applicable to dynamic QR)                  | "VALID"                                                                                                      |
| <code>qrCodeUrl</code>       | String   | Embedded URL in QR                                                                                  | "https://dev-rm-api.ap.ngrok.io/payment/unified?code=c8ff3df0605a5f20cd6476661072eade"                       |
| <code>redirectUrl</code>     | String   | Redirect URL after QR payment is made                                                               | "https://www.apple.com/my/iphone/"                                                                           |
| <code>order</code>           | Object   | Order object                                                                                        | (Refer to explanation below)                                                                                 |
| <code>createdAt</code>       | DateTime | Creation date time of transaction                                                                   | "2018-03-21T06:41:22Z"                                                                                       |
| <code>updatedAt</code>       | DateTime | Last update date time of transaction                                                                | "2018-03-21T06:41:22Z"                                                                                       |

<strong>Store object (`"store"`):</strong>

| Parameter                 | Type              | Description                                     | Example                                             |
| ------------------------- | ----------------- | ----------------------------------------------- | --------------------------------------------------- |
| <code>id</code>           | String            | Store ID                                        | "6170506694335521334"                               |
| <code>name</code>         | String            | Store Name                                      | "REVENUE MONSTER"                                   |
| <code>addressLine1</code> | String            | Store Address 1                                 | "B-5-30, 5th Floor, Block Bougainvillea,"           |
| <code>addressLine2</code> | String            | Store Address 2                                 | "PJU 6A, Lebuhraya SPRINT, 10 Boulevard,"           |
| <code>postCode</code>     | String            | Postcode of store                               | "47400"                                             |
| <code>city</code>         | String            | City of store                                   | "Petaling Jaya"                                     |
| <code>state</code>        | String            | State of store                                  | "Selangor"                                          |
| <code>country</code>      | String            | Country of store                                | "Malaysia"                                          |
| <code>countryCode</code>  | String            | Country code of store contact number            | "60"                                                |
| <code>phoneNumber</code>  | String            | Phone number of store                           | "377334080"                                         |
| <code>geoLocation</code>  | Object of [Float] | Geo Location (latitude and longtitude) of store | {"latitude": 3.1349857, "longtitude": 101.6136659 } |
| <code>status</code>       | String            | Current status of store                         | "ACTIVE"                                            |
| <code>createdAt</code>    | DateTime          | Creation date time of store                     | "2018-02-12T08:53:13Z"                              |
| <code>updatedAt</code>    | DateTime          | Last update date time of store                  | "2018-02-12T08:53:13Z"                              |

<strong>Expiry object (`"expiry"`):</strong>

| Parameter              | Type     | Description                                                                               | Example                            |
| ---------------------- | -------- | ----------------------------------------------------------------------------------------- | ---------------------------------- |
| <code>type</code>      | String   | "DYNAMIC" (days from now), "FIX" (specific fixed date) or "PERMANENT" (never expire)      | "PERMANENT"                        |
| <code>day</code>       | Uint     | Only required by "DYNAMIC" expiry type. To indicate number of days from now until expiry. | 3                                  |
| <code>expiredAt</code> | DateTime | Only required by "FIXED". To indicate specific expiry date.                               | "2020-10-07T17:44:26.679908+08:00" |

<strong>Order object (`"order"`):</strong>

| Parameter                     | Type   | Description                     | Example                                 |
| ----------------------------- | ------ | ------------------------------- | --------------------------------------- |
| <code>details</code>          | String | Order details, max: 600         | "1 x iPhone X; 2 x SAMSUNG S8"          |
| <code>title</code>            | String | Order title, max: 32            | "Sales"                                 |
| <code> additionalData </code> | String | Order additional data, max: 128 | "Sales for customer xxx at branch xxx." |

<!---=================================--->
<!---Get Transaction QR Code URL --->
<!---=================================--->

##Get Transaction QR Code URL
**Method <span style="color:Green" , bold >`GET`</span>**

<code>https://sb-open.revenuemonster.my/v3/payment/transaction/qrcodes?order[]=-createdAt&limit=1&filter={"type":"STATIC", "expiry.type": "PERMANENT"}</code>

To get all QR Code(s) generated previously in the system.

> Example Request

```json
curl --location --request GET "https://sb-open.revenuemonster.my/v3/payment/transaction/qrcodes" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{
	\"amount\": 100,
	\"currencyType\": \"MYR\",
	\"method\": [\"WECHATPAY\"],
	\"expiry\": {
	    \"type\": \"PERMANENT\"
	},
	\"quantity\": 2,
	\"type\": \"STATIC\",
	\"storeId\": \"10946114768247530\",
	\"isPreFillAmount\": true
}"
```

**_REQUEST_**

<strong>Request Parameters:</strong>

_Note: No request parameter is required for this endpoint_

**_RESPONSE_**

<strong>Response Parameters:</strong>

| Parameter          | Type     | Description                                                                                               | Example                      |
| ------------------ | -------- | --------------------------------------------------------------------------------------------------------- | ---------------------------- |
| <code>items</code> | []Object | Transaction object                                                                                        | (Refer to explanation below) |
| <code>code</code>  | String   | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"                    |

> Example Respond

```json
{
  "items": [
    {
      "storeId": "10946114768247530",
      "type": "STATIC",
      "isPreFillAmount": true,
      "currencyType": "MYR",
      "amount": 100,
      "platform": "PORTAL",
      "method": ["WECHATPAY"],
      "expiry": {
        "type": "PERMANENT",
        "day": 0,
        "expiredAt": "2050-12-31T23:59:59Z"
      },
      "code": "a669adc3b06fe5cef977cc762f40ce8c",
      "status": "VALID",
      "qrCodeUrl": "https://dev-rm-api.ap.ngrok.io/payment/unified?code=a669adc3b06fe5cef977cc762f40ce8c",
      "createdAt": "2018-06-25T02:29:28Z",
      "updatedAt": "2018-06-25T02:29:28Z"
    },
    {
      "storeId": "10946114768247530",
      "type": "STATIC",
      "isPreFillAmount": true,
      "currencyType": "MYR",
      "amount": 100,
      "platform": "PORTAL",
      "method": ["WECHATPAY"],
      "expiry": {
        "type": "PERMANENT",
        "day": 0,
        "expiredAt": "2050-12-31T23:59:59Z"
      },
      "code": "d54b69122f59ea46ac3fced769854ec2",
      "status": "VALID",
      "qrCodeUrl": "https://dev-rm-api.ap.ngrok.io/payment/unified?code=d54b69122f59ea46ac3fced769854ec2",
      "createdAt": "2018-06-25T02:29:53Z",
      "updatedAt": "2018-06-25T02:29:53Z"
    },
    {
      "storeId": "10946114768247530",
      "type": "STATIC",
      "isPreFillAmount": true,
      "currencyType": "MYR",
      "amount": 100,
      "platform": "PORTAL",
      "method": ["WECHATPAY"],
      "expiry": {
        "type": "PERMANENT",
        "day": 0,
        "expiredAt": "2050-12-31T23:59:59Z"
      },
      "code": "e794902fbcb62c59b8d9cf270a5e505a",
      "status": "VALID",
      "qrCodeUrl": "https://dev-rm-api.ap.ngrok.io/payment/unified?code=e794902fbcb62c59b8d9cf270a5e505a",
      "createdAt": "2018-06-25T02:28:24Z",
      "updatedAt": "2018-06-25T02:28:24Z"
    }
  ],
  "code": "SUCCESS",
  "meta": {
    "count": 3
  }
}
```

<strong>Transaction object array (`"items"`):</strong>

| Parameter                    | Type     | Description                                                                                         | Example                                                                                                      |
| ---------------------------- | -------- | --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| <code>storeId</code>         | String   | ID of store                                                                                         | 10946114768247530                                                                                            |
| <code>type</code>            | String   | "DYNAMIC" (days from now), "FIXED" (specific fixed date) or "PERMANENT" (never expire)              | "PERMANENT"                                                                                                  |
| <code>isPreFillAmount</code> | Bool     | To indicate QR code has pre-fill amount                                                             | true                                                                                                         |
| <code>currencyType</code>    | String   | Currency notation                                                                                   | "MYR"                                                                                                        |
| <code>amount</code>          | Uint     | Amount of order in cent. Only required when "isPrefillAmount" = true.                               | 100                                                                                                          |
| <code>platform</code>        | String   | "OPEN_API" (generated through API calls) or "PORTAL" (generated through merchant portal)            | "PORTAL"                                                                                                     |
| <code>method</code>          | []String | Wallet provider for payment, supports "WECHATPAY", "PRESTO" , "BOOST" , "ALIPAY_CN" , "GRABPAY_MY". | ["WECHATPAY","WECHATPAY_MY", <br/> "WECHATPAY_CN","PRESTO_MY",<br/>"BOOST_MY",<br/>"ALIPAY_CN","GRABPAY_MY"] |
| <code>expiry</code>          | String   | Object of expiry                                                                                    | (Refer to explanation above)                                                                                 |
| <code>code</code>            | String   | Embedded code in QR                                                                                 | "c8ff3df0605a5f20cd6476661072eade"                                                                           |
| <code>status</code>          | String   | "VALID" (always valid for static QR) or "REDEEMED" (only applicable to dynamic QR)                  | "VALID"                                                                                                      |
| <code>qrCodeUrl</code>       | String   | Embedded URL in QR                                                                                  | "https://dev-rm-api.ap.ngrok.io/payment/unified?code=c8ff3df0605a5f20cd6476661072eade"                       |
| <code>redirectUrl</code>     | String   | Redirect URL after QR payment is made                                                               | "https://www.apple.com/my/iphone/"                                                                           |
| <code>createdAt</code>       | DateTime | Creation date time of transaction                                                                   | "2018-03-21T06:41:22Z"                                                                                       |
| <code>updatedAt</code>       | DateTime | Last update date time of transaction                                                                | "2018-03-21T06:41:22Z"                                                                                       |

<strong>Expiry object (`"expiry"`):</strong>

| Parameter              | Type     | Description                                                                               | Example                            |
| ---------------------- | -------- | ----------------------------------------------------------------------------------------- | ---------------------------------- |
| <code>type</code>      | String   | "DYNAMIC" (days from now), "FIX" (specific fixed date) or "PERMANENT" (never expire)      | "PERMANENT"                        |
| <code>day</code>       | Uint     | Only required by "DYNAMIC" expiry type. To indicate number of days from now until expiry. | 3                                  |
| <code>expiredAt</code> | DateTime | Only required by "FIXED". To indicate specific expiry date.                               | "2020-10-07T17:44:26.679908+08:00" |

<strong>Database object (`"meta"`):</strong>

| Parameter          | Type | Description         | Example |
| ------------------ | ---- | ------------------- | ------- |
| <code>count</code> | Int  | Current page record | 1       |

<!---==================================--->
<!---Get Transaction QRCode URL By Code --->
<!---==================================--->

##Get Transaction QRCode URL By Code
**Method <span style="color:Green" , bold >`GET`</span>**

<code>https://sb-open.revenuemonster.my/v3/payment/transaction/qrcode/5413b4583a9440dd351b2dde0c0ea166</code>

To get specific QR Code generated previously in the system, by passing in code in query parameter (/qrcode/...).

> Example Request

```json
curl --location --request GET "https://sb-open.revenuemonster.my/v3/payment/transaction/qrcode/a669adc3b06fe5cef977cc762f40ce8c" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{
	\"amount\": 100,
	\"currencyType\": \"MYR\",
	\"method\": [\"WECHATPAY\"],
	\"expiry\": {
	    \"type\": \"PERMANENT\"
	},
	\"quantity\": 2,
	\"type\": \"STATIC\",
	\"storeId\": \"10946114768247530\",
	\"isPreFillAmount\": true
}"
```

**_REQUEST_**

<strong>Request Parameters:</strong>

_Note: No request parameter is required for this endpoint_

**_RESPONSE_**

<strong>Response Parameters:</strong>

| Parameter         | Type   | Description                                                                                               | Example                      |
| ----------------- | ------ | --------------------------------------------------------------------------------------------------------- | ---------------------------- |
| <code>item</code> | Object | Transaction object                                                                                        | (Refer to explanation below) |
| <code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"                    |

> Example Respond

```json
{
  "item": {
    "storeId": "10946114768247530",
    "type": "STATIC",
    "isPreFillAmount": true,
    "currencyType": "MYR",
    "amount": 100,
    "platform": "PORTAL",
    "method": ["WECHATPAY"],
    "expiry": {
      "type": "PERMANENT",
      "day": 0,
      "expiredAt": "2050-12-31T23:59:59Z"
    },
    "code": "a669adc3b06fe5cef977cc762f40ce8c",
    "status": "VALID",
    "qrCodeUrl": "https://dev-rm-api.ap.ngrok.io/payment/unified?code=a669adc3b06fe5cef977cc762f40ce8c",
    "createdAt": "2018-06-25T02:29:28Z",
    "updatedAt": "2018-06-25T02:29:28Z"
  },
  "code": "SUCCESS"
}
```

<strong>Transaction object (`"item"`):</strong>

| Parameter                    | Type     | Description                                                                                         | Example                                                                                                      |
| ---------------------------- | -------- | --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| <code>storeId</code>         | String   | ID of store                                                                                         | 10946114768247530                                                                                            |
| <code>type</code>            | String   | "DYNAMIC" (days from now), "FIXED" (specific fixed date) or "PERMANENT" (never expire)              | "PERMANENT"                                                                                                  |
| <code>isPreFillAmount</code> | Bool     | To indicate QR code has pre-fill amount                                                             | true                                                                                                         |
| <code>currencyType</code>    | String   | Currency notation                                                                                   | "MYR"                                                                                                        |
| <code>amount</code>          | Uint     | Amount of order in cent. Only required when "isPrefillAmount" = true.                               | 100                                                                                                          |
| <code>platform</code>        | String   | "OPEN_API" (generated through API calls) or "PORTAL" (generated through merchant portal)            | "PORTAL"                                                                                                     |
| <code>method</code>          | []String | Wallet provider for payment, supports "WECHATPAY", "PRESTO" , "BOOST" , "ALIPAY_CN" , "GRABPAY_MY". | ["WECHATPAY","WECHATPAY_MY", <br/> "WECHATPAY_CN","PRESTO_MY",<br/>"BOOST_MY",<br/>"ALIPAY_CN","GRABPAY_MY"] |
| <code>expiry</code>          | String   | Object of expiry                                                                                    | (Refer to explanation above)                                                                                 |
| <code>code</code>            | String   | Embedded code in QR                                                                                 | "c8ff3df0605a5f20cd6476661072eade"                                                                           |
| <code>status</code>          | String   | "VALID" (always valid for static QR) or "REDEEMED" (only applicable to dynamic QR)                  | "VALID"                                                                                                      |
| <code>qrCodeUrl</code>       | String   | Embedded URL in QR                                                                                  | "https://dev-rm-api.ap.ngrok.io/payment/unified?code=c8ff3df0605a5f20cd6476661072eade"                       |
| <code>redirectUrl</code>     | String   | Redirect URL after QR payment is made                                                               | "https://www.apple.com/my/iphone/"                                                                           |
| <code>createdAt</code>       | DateTime | Creation date time of transaction                                                                   | "2018-03-21T06:41:22Z"                                                                                       |
| <code>updatedAt</code>       | DateTime | Last update date time of transaction                                                                | "2018-03-21T06:41:22Z"                                                                                       |

<strong>Expiry object (`"expiry"`):</strong>

| Parameter              | Type     | Description                                                                               | Example                            |
| ---------------------- | -------- | ----------------------------------------------------------------------------------------- | ---------------------------------- |
| <code>type</code>      | String   | "DYNAMIC" (days from now), "FIX" (specific fixed date) or "PERMANENT" (never expire)      | "PERMANENT"                        |
| <code>day</code>       | Uint     | Only required by "DYNAMIC" expiry type. To indicate number of days from now until expiry. | 3                                  |
| <code>expiredAt</code> | DateTime | Only required by "FIXED". To indicate specific expiry date.                               | "2020-10-07T17:44:26.679908+08:00" |

<!---=================================--->
<!---Get Transaction By Code --->
<!---=================================--->

##Get Transactions By Code
**Method <span style="color:Green" , bold >`GET`</span>**

<code>https://sb-open.revenuemonster.my/v3/payment/transaction/qrcode/5413b4583a9440dd351b2dde0c0ea166/transactions</code>

To get all transactions under existing QR code, by passing in code in query parameter (/qrcode/.../transactions).

> Example Request

```json
curl --location --request GET "https://sb-open.revenuemonster.my/v3/payment/transaction/qrcode/39d1f014eade17aa77fb2aaa6a4e6afb/transactions" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{
  \"amount\": 100,
  \"currencyType\": \"MYR\",
  \"method\": [\"WECHATPAY\"],
  \"expiry\": {
      \"type\": \"PERMANENT\"
  },
  \"quantity\": 2,
  \"type\": \"STATIC\",
  \"storeId\": \"10946114768247530\",
  \"isPreFillAmount\": true
}"
```

**_REQUEST_**

<strong>Request Parameters:</strong>

_Note: No request parameter is required for this endpoint_

**_RESPONSE_**

<strong>Response Parameters:</strong>

| Parameter          | Type     | Description                                                                                               | Example                      |
| ------------------ | -------- | --------------------------------------------------------------------------------------------------------- | ---------------------------- |
| <code>items</code> | []Object | Transaction object                                                                                        | (Refer to explanation below) |
| <code>code</code>  | String   | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"                    |

> Example Respond

```json
{
  "items": [
    {
      "store": {
        "id": "10946114768247530",
        "name": "One Utama",
        "addressLine1": "ANYTHING",
        "addressLine2": "",
        "postCode": "48484",
        "city": "KUALA LUMPUR",
        "state": "W.P. KUALA LUMPUR",
        "country": "MALAYSIA",
        "countryCode": "60",
        "phoneNumber": "12312341234",
        "geoLocation": {
          "latitude": 0,
          "longitude": 0
        },
        "status": "ACTIVE",
        "createdAt": "2018-06-03T08:53:48Z",
        "updatedAt": "2018-06-03T08:53:48Z"
      },
      "referenceId": "",
      "transactionId": "180802093420010425899434",
      "order": {
        "id": "180802093420010425899434",
        "title": "title",
        "detail": "detail",
        "additionalData": "",
        "amount": 100
      },
      "terminalId": "",
      "currencyType": "MYR",
      "balanceAmount": 0,
      "platform": "OPEN_API",
      "method": "WECHATPAY",
      "error": {
        "message": "Payment timeout"
      },
      "transactionAt": "2018-08-02T09:34:53Z",
      "type": "QUICK_PAY",
      "status": "FAILED",
      "region": "MALAYSIA",
      "createdAt": "2018-08-02T09:34:20Z",
      "updatedAt": "2018-08-02T09:34:53Z"
    }
  ],
  "code": "SUCCESS",
  "meta": {
    "count": 1
  }
}
```

<strong>Transaction object array (`"items"`):</strong>

| Parameter                  | Type     | Description                                                                                                                                | Example                                                                                                      |
| -------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| <code>store</code>         | Object   | Store object                                                                                                                               | (Refer to explanation below)                                                                                 |
| <code>referenceId</code>   | String   | Transaction ID (from WeChat server)                                                                                                        | ""                                                                                                           |
| <code>transactionId</code> | String   | Transaction ID (from RM server)                                                                                                            | "152161448229438994"                                                                                         |
| <code>order</code>         | Object   | Order object                                                                                                                               | (Refer to explanation below)                                                                                 |
| <code>terminalId</code>    | String   | ID of terminal (Optional, if the payment is made through terminal)                                                                         | ""                                                                                                           |
| <code>currencyType</code>  | String   | Currency notation                                                                                                                          | "MYR"                                                                                                        |
| <code>balanceAmount</code> | Uint     | Total available amount (= total received amount - total refunded amount). In this case, amount 100 is failed, so no amount is received.    | 0                                                                                                            |
| <code>platform</code>      | String   | "OPEN_API" (generated through API calls) or "PORTAL" (generated through merchant portal)                                                   | "OPEN_API"                                                                                                   |
| <code>method</code>        | String   | Wallet provider for payment, supports "WECHATPAY", "PRESTO" , "BOOST" , "ALIPAY_CN" , "GRABPAY_MY".                                        | ["WECHATPAY","WECHATPAY_MY", <br/> "WECHATPAY_CN","PRESTO_MY",<br/>"BOOST_MY",<br/>"ALIPAY_CN","GRABPAY_MY"] |
| <code>error</code>         | String   | Error message only if transaction failed (optional)                                                                                        | {message": "Payment timeout"}                                                                                |
| <code>transactionAt</code> | DateTime | Transaction date time (from wallet server)                                                                                                 | "2018-08-02T09:34:53"                                                                                        |
| <code>type</code>          | String   | Currently only support "QUICKPAY"                                                                                                          | "QUICKPAY"                                                                                                   |
| <code>status</code>        | String   | Transaction status returned from wallet server, "SUCCESS" or "IN_PROCESS" or "FAILED". "IN_PROCESS" means user scanned and making payment. | "FAILED"                                                                                                     |
| <code>region</code>        | String   | Region of wallet, "MALAYSIA" or "CHINA"                                                                                                    | "MALAYSIA"                                                                                                   |
| <code>createdAt</code>     | DateTime | Creation date time of transaction (from RM server)                                                                                         | "2018-08-02T09:34:53"                                                                                        |
| <code>updatedAt</code>     | DateTime | Last update date time of transaction                                                                                                       | "2018-08-02T09:34:53"                                                                                        |

<strong>Store object (`"store"`):</strong>

| Parameter                 | Type               | Description                                     | Example                                   |
| ------------------------- | ------------------ | ----------------------------------------------- | ----------------------------------------- |
| <code>id</code>           | String             | Store ID                                        | "6170506694335521334"                     |
| <code>name</code>         | String             | Store Name                                      | "REVENUE MONSTER"                         |
| <code>addressLine1</code> | String             | Store Address 1                                 | "B-5-30, 5th Floor, Block Bougainvillea," |
| <code>addressLine2</code> | String             | Store Address 2                                 | "PJU 6A, Lebuhraya SPRINT, 10 Boulevard," |
| <code>postCode</code>     | String             | Postcode of store                               | "47400"                                   |
| <code>city</code>         | String             | City of store                                   | "Petaling Jaya"                           |
| <code>state</code>        | String             | State of store                                  | "Selangor"                                |
| <code>country</code>      | String             | Country of store                                | "Malaysia"                                |
| <code>countryCode</code>  | String             | Country code of store contact number            | "60"                                      |
| <code>phoneNumber</code>  | String             | Phone number of store                           | "377334080"                               |
| <code>geoLocation</code>  | Object of [String] | Geo Location (latitude and longtitude) of store | {"Lat": 3.1349857, "Lng": 101.6136659 }   |
| <code>status</code>       | String             | Current status of store                         | "ACTIVE"                                  |
| <code>createdAt</code>    | DateTime           | Creation date time of store                     | "2018-02-12T08:53:13Z"                    |
| <code>updatedAt</code>    | DateTime           | Last update date time of store                  | "2018-02-12T08:53:13Z"                    |

<strong>Database object (`"meta"`):</strong>

| Parameter          | Type | Description         | Example |
| ------------------ | ---- | ------------------- | ------- |
| <code>count</code> | Int  | Current page record | 1       |
