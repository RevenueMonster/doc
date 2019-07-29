#Payment-Quickpay QR#

Scenarios:<br>

1. EDC/Smart Payment Terminal <br>
2. POS(point-of-sales) Payment Integration

To make payments with `Quick Pay`. Merchant to scan user's wallet.

- Scope: `manage_payment`
- Authentication: Access token obtained from [Generate Access Token](https://doc.revenuemonster.my/#66368026-71ee-4640-8ad7-208f843c6d6c) into `Authorization` header value as `Bearer [access_token]`.

- If merchant has not entered `Webhook URL` and/or `Client Public Key` in Merchant Portal, system will throw **error** as below:

<aside class="warning"> <strong>Example :</strong>
<br>
<strong>
{ <br>
  "error": { <br>
        "code": "CLIENT_PRODUCT_NOT_SETUP",<br>
        "message": "Developer application product not setup"<br>
        } <br />
}
</strong>
</aside>

<!--============--->
<!--Quick Pay--->
<!--============--->

##Quick Pay
**Method <span style="color:Orange" , bold >`POST`</span>**

`https://sb-open.revenuemonster.my/v3/payment/quickpay`

To initiate Quick Pay by merchant scanning user's QR code.

> Example Request

```json

curl --location --request POST "https://sb-open.revenuemonster.my/v3/payment/quickpay" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{
   \"authCode\":\"151261311797136005\",
   \"order\":{
      \"amount\":100,
      \"currencyType\":\"MYR\",
      \"id\":\"12344333233404\",
      \"title\":\"title\",
      \"detail\":\"desc\",
      \"additonalData\":\"API Test\"
   },
   \"ipAddress\":\"175.143.101.229\",
   \"storeId\":\"10946114768247530\"
}"
```

**_REQUEST_**

<strong>Request Parameters:</strong>

| Parameter               | Type   | Required | Description                                            | Example                      |
| ----------------------- | ------ | -------- | ------------------------------------------------------ | ---------------------------- |
| <code>authCode</code>   | String | Yes      | Auth code of QR code/barcode being scanned. Length: 18 | "134850717797247290"         |
| <code>order</code>      | Object | Yes      | Object of order                                        | (Refer to explanation below) |
| <code>ipAddress</code>  | String | Yes      | IP address of terminal/application for payment         | "8.8.8.8"                    |
| <code>terminalId</code> | String | No       | ID of terminal for payment                             | "19382734937293"             |
| <code>storeId</code>    | String | Yes      | ID of the store                                        | "6170506694335521334"        |

> Example Respond

```json
{
  "item": {
    "store": {
      "id": "10946114768247530",
      "name": "One Utama",
      "addressLine1": "200, ABCD",
      "addressLine2": "",
      "postCode": "48482",
      "city": "AMPANG",
      "state": "W.P. KUALA LUMPUR",
      "country": "MALAYSIA",
      "countryCode": "60",
      "phoneNumber": "12312341234",
      "geoLocation": {
        "latitude": 0,
        "longitude": 0
      },
      "status": "ACTIVE",
      "createdAt": "2018-06-28T03:24:52Z",
      "updatedAt": "2018-06-28T03:24:52Z"
    },
    "referenceId": "1010014200000026201807306110047699",
    "transactionId": "180730103559010434619271",
    "order": {
      "id": "12344333233404",
      "title": "title",
      "detail": "desc",
      "amount": 100
    },
    "terminalId": "19382734937293",
    "payee": {
      "userId": "o74f0wsssZBWis4rJWyDCWmEF-ig"
    },
    "currencyType": "MYR",
    "balanceAmount": 100,
    "platform": "OPEN_API",
    "method": "WECHATPAY",
    "transactionAt": "2018-07-30T10:36:01.515328338Z",
    "type": "QUICK_PAY",
    "status": "SUCCESS",
    "region": "MALAYSIA",
    "createdAt": "2018-07-30T10:35:59.233482384Z",
    "updatedAt": "2018-07-30T10:36:01.515328459Z"
  },
  "code": "SUCCESS"
}
```

<strong>Order object (`"order"`):</strong>

| Parameter                   | Type   | Required | Description                                         | Example                        |
| --------------------------- | ------ | -------- | --------------------------------------------------- | ------------------------------ |
| <code>id</code>             | String | Yes      | Order ID (from Merchant), max: 24                   | "134850717797247290"           |
| <code>title</code>          | String | Yes      | Order title, max: 32                                | "Sales"                        |
| <code>details</code>        | String | Yes      | Order details, max: 600                             | "1 x iPhone X; 2 x SAMSUNG S8" |
| <code>additionalData</code> | String | Yes      | For merchant's remark, max 128                      | ""                             |
| <code>amount</code>         | Uint   | Yes      | Amount of order in cent (min RM 0.10 or amount: 10) | 100                            |

**_RESPONSE_**

<strong>Response Parameters: </strong>

| Parameter          | Type   | Description                                                                                               | Example                      |
| ------------------ | ------ | --------------------------------------------------------------------------------------------------------- | ---------------------------- |
| <code>items</code> | Object | Transaction object                                                                                        | (Refer to explanation below) |
| <code>code</code>  | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"                    |

<strong>Transaction object (`"item"`):</strong>

| Parameter                  | Type     | Description                                                                                              | Example                                    |
| -------------------------- | -------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| <code>store</code>         | Object   | Store object                                                                                             | (Refer to explanation below)               |
| <code>referenceId</code>   | String   | Transaction ID (from WeChat server)                                                                      | ""                                         |
| <code>transactionId</code> | String   | Transaction ID (from RM server)                                                                          | "152161448229438994"                       |
| <code>order</code>         | Object   | Order object                                                                                             | (Refer to explanation below)               |
| <code>payee</code>         | Object   | Object of userID made payment (payment sender)                                                           | {"userId": "o74f0wjjzv9eKRu1fccrZswVFnOQ"} |
| <code>currencyType</code>  | String   | Currency notation (currently only support `MYR`)                                                         | "MYR"                                      |
| <code>platform</code>      | String   | Currently only support "OPEN_API"                                                                        | "OPEN_API"                                 |
| <code>method</code>        | String   | Currently only support "WECHATPAY" , "PRESTO" , "BOOST" , "TNG" , "MAYBANK" , "ALIPAY_CN" , "GRABPAY_MY" | ALL                                        |
| <code>type</code>          | String   | Currently only support "QUICKPAY"                                                                        | "QUICKPAY"                                 |
| <code>status</code>        | String   | Status returned from WeChat server                                                                       | "SUCCESS"                                  |
| <code>error</code>         | String   | (Refer `Appendix: Error Codes`)                                                                          | {}                                         |
| <code>createdAt</code>     | DateTime | Creation date time of transaction                                                                        | "2018-03-21T06:41:22Z"                     |
| <code>updatedAt</code>     | DateTime | Last update date time of transaction                                                                     | "2018-03-21T06:41:22Z"                     |

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

<strong>Order object (`"order"`):</strong>

| Parameter            | Type   | Description                                         | Example                        |
| -------------------- | ------ | --------------------------------------------------- | ------------------------------ |
| <code>id</code>      | String | Order ID (from Merchant), max: 24                   | "134850717797247290"           |
| <code>title</code>   | String | Order title, max: 32                                | "Sales"                        |
| <code>details</code> | String | Order details, max: 600                             | "1 x iPhone X; 2 x SAMSUNG S8" |
| <code>amount</code>  | Uint   | Amount of order in cent (min RM 0.10 or amount: 10) | 100                            |

<!--============--->
<!--Refund--->
<!--============--->

##Refund

**Method <span style="color:Orange" , bold >`POST`</span>**

`https://sb-open.revenuemonster.my/v3/payment/refund`

Refund is to get funds returned to the customer after settlement. (After the money is settled to the merchant.)

> Example Request

```json
curl --location --request POST "https://sb-open.revenuemonster.my/v3/payment/refund" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 ZtQhyfkgMLY2FCxQeVQPljczzijPoC7zWH087erdAm1h2x2A0B+GQ9Fk89VbvMB9400m8SFBDRz5XgEVaqPh7Q==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1527407052" \
  --data "{
  \"transactionId\": \"180730103903010431152179\",
  \"refund\": {
    \"type\": \"FULL\",
    \"currencyType\": \"MYR\",
    \"amount\": 100
  },
  \"reason\": \"test\"
}"
```

**_REQUEST_**

<strong>Request Parameters:</strong>

| Parameter                  | Type   | Required | Description                                    | Example                      |
| -------------------------- | ------ | -------- | ---------------------------------------------- | ---------------------------- |
| <code>transactionId</code> | String | Yes      | Transaction ID generated from Revenue Monster. | "180730103903010431152179"   |
| <code>refund</code>        | Object | Yes      | Object of refund                               | (Refer to explanation below) |
| <code>reason</code>        | String | Yes      | Refund reason                                  | "Wrong Item"                 |

<strong>Refund object (`"refund"`):</strong>

| Parameter                 | Type   | Required | Description                                                                             | Example |
| ------------------------- | ------ | -------- | --------------------------------------------------------------------------------------- | ------- |
| <code>type</code>         | String | Yes      | Fully or partial refund. "FULL"/"PARTIAL" (**currenty for sandbox can partial refund**) | "FULL"  |
| <code>currencyType</code> | String | Yes      | Currency notation (currently only support `MYR`)                                        | "MYR"   |
| <code>amount</code>       | Uint   | Yes      | Amount of order in cent                                                                 | 100     |

> Example Respond

```json
{
  "item": {
    "store": {
      "id": "10946114768247530",
      "name": "One Utama",
      "addressLine1": "200, ABCD",
      "addressLine2": "",
      "postCode": "48482",
      "city": "AMPANG",
      "state": "W.P. KUALA LUMPUR",
      "country": "MALAYSIA",
      "countryCode": "60",
      "phoneNumber": "12312341234",
      "geoLocation": {
        "latitude": 0,
        "longitude": 0
      },
      "status": "ACTIVE",
      "createdAt": "2018-06-28T03:24:52Z",
      "updatedAt": "2018-06-28T03:24:52Z"
    },
    "referenceId": "1010014200000026201807306110047703",
    "transactionId": "180730103903010431152179",
    "order": {
      "id": "12344333233414",
      "title": "title",
      "detail": "desc",
      "amount": 100
    },
    "terminalId": "19382734937293",
    "payee": {
      "userId": "o74f0wsssZBWis4rJWyDCWmEF-ig"
    },
    "currencyType": "MYR",
    "balanceAmount": 0,
    "platform": "OPEN_API",
    "method": "WECHATPAY",
    "transactionAt": "2018-07-30T10:39:06Z",
    "type": "QUICK_PAY",
    "status": "FULL_REFUNDED",
    "region": "MALAYSIA",
    "createdAt": "2018-07-30T10:39:03Z",
    "updatedAt": "2018-07-30T10:39:37.462943554Z"
  },
  "code": "SUCCESS"
}
```

**_RESPONSE_**

<strong>Response Parameters:</strong>

| Parameter          | Type   | Description                                                                                               | Example                      |
| ------------------ | ------ | --------------------------------------------------------------------------------------------------------- | ---------------------------- |
| <code>items</code> | Object | Transaction object                                                                                        | (Refer to explanation below) |
| <code>code</code>  | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"                    |

<strong>Transaction object (`"item"`):</strong>

| Parameter                  | Type     | Description                                                                                              | Example                                    |
| -------------------------- | -------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| <code>store</code>         | Object   | Store object                                                                                             | (Refer to explanation below)               |
| <code>referenceId</code>   | String   | Transaction ID (from WeChat server)                                                                      | ""                                         |
| <code>transactionId</code> | String   | Transaction ID (from RM server)                                                                          | "152161448229438994"                       |
| <code>order</code>         | Object   | Order object                                                                                             | (Refer to explanation below)               |
| <code>payee</code>         | Object   | Object of userID made payment (payment sender)                                                           | {"userId": "o74f0wjjzv9eKRu1fccrZswVFnOQ"} |
| <code>platform</code>      | String   | Currently only support "OPEN_API"                                                                        | "OPEN_API"                                 |
| <code>method</code>        | String   | Currently only support "WECHATPAY" , "PRESTO" , "BOOST" , "TNG" , "MAYBANK" , "ALIPAY_CN" , "GRABPAY_MY" | ALL                                        |
| <code>type</code>          | String   | Currently only support "QUICKPAY"                                                                        | "QUICKPAY"                                 |
| <code>status</code>        | String   | Status returned from WeChat server                                                                       | "SUCCESS"                                  |
| <code>error</code>         | String   | (Refer `Appendix: Error Codes`)                                                                          | {}                                         |
| <code>createdAt</code>     | DateTime | Creation date time of transaction                                                                        | "2018-03-21T06:41:22Z"                     |
| <code>updatedAt</code>     | DateTime | Last update date time of transaction                                                                     | "2018-03-21T06:41:22Z"                     |

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

<strong>Order object (`"order"`):</strong>

| Parameter                   | Type   | Description                                      | Example                        |
| --------------------------- | ------ | ------------------------------------------------ | ------------------------------ |
| <code>id</code>             | String | Order ID (from Merchant), max: 24                | "134850717797247290"           |
| <code>title</code>          | String | Order title, max: 32                             | "Sales"                        |
| <code>details</code>        | String | Order details, max: 600                          | "1 x iPhone X; 2 x SAMSUNG S8" |
| <code>additionalData</code> | String | For merchant's remark, max 128                   | ""                             |
| <code>currencyType</code>   | String | Currency notation (currently only support `MYR`) | "MYR"                          |
| <code>amount</code>         | Uint   | Amount of order in cent                          | 100                            |

<!--============--->
<!--Reverse--->
<!--============--->

##Reverse

**Method <span style="color:Orange" , bold >`POST`</span>**

`https://sb-open.revenuemonster.my/v3/payment/reverse`

Refund is to get funds returned to customer before settlement. (Before money is settled to merchant.)

Note: If transaction is timed out, should perform reverse order before creating new transaction. This is to make sure no double charge.

> Example Request

```json
curl --location --request POST "https://sb-open.revenuemonster.my/v3/payment/reverse" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 ZtQhyfkgMLY2FCxQeVQPljczzijPoC7zWH087erdAm1h2x2A0B+GQ9Fk89VbvMB9400m8SFBDRz5XgEVaqPh7Q==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1527407052" \
  --data "{
  \"orderId\": \"12344333233404\"
}"
```

**_REQUEST_**

<strong>Request Parameters:</strong>

| Parameter            | Type   | Required | Description                       | Example              |
| -------------------- | ------ | -------- | --------------------------------- | -------------------- |
| <code>orderId</code> | String | Yes      | Order ID (from Merchant), max: 24 | "134850717797247290" |

**_RESPONSE_**

<strong>Response Parameters:</strong>

| Parameter          | Type   | Description                                                                                               | Example                      |
| ------------------ | ------ | --------------------------------------------------------------------------------------------------------- | ---------------------------- |
| <code>items</code> | Object | Transaction object                                                                                        | (Refer to explanation below) |
| <code>code</code>  | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"                    |

> Example Respond

```json
{
  "item": {
    "referenceId": "1010014200000026201807306110047699",
    "transactionId": "180730103559010434619271",
    "order": {
      "id": "12344333233404",
      "title": "title",
      "detail": "desc",
      "amount": 100
    },
    "terminalId": "19382734937293",
    "payee": {
      "userId": "o74f0wsssZBWis4rJWyDCWmEF-ig"
    },
    "currencyType": "MYR",
    "balanceAmount": 0,
    "platform": "OPEN_API",
    "method": "WECHATPAY",
    "transactionAt": "2018-07-30T10:36:01Z",
    "type": "QUICK_PAY",
    "status": "REVERSED",
    "region": "MALAYSIA",
    "createdAt": "2018-07-30T10:35:59Z",
    "updatedAt": "2018-07-30T10:37:24.376379089Z"
  },
  "code": "SUCCESS"
}
```

<strong>Transaction object (`"item"`):</strong>

| Parameter                  | Type     | Description                                                                                              | Example                                    |
| -------------------------- | -------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| <code>store</code>         | Object   | Store object                                                                                             | (Refer to explanation below)               |
| <code>referenceId</code>   | String   | Transaction ID (from WeChat server)                                                                      | ""                                         |
| <code>transactionId</code> | String   | Transaction ID (from RM server)                                                                          | "152161448229438994"                       |
| <code>order</code>         | Object   | Order object                                                                                             | (Refer to explanation below)               |
| <code>payee</code>         | Object   | Object of userID made payment (payment sender)                                                           | {"userId": "o74f0wjjzv9eKRu1fccrZswVFnOQ"} |
| <code>platform</code>      | String   | Currently only support "OPEN_API"                                                                        | "OPEN_API"                                 |
| <code>method</code>        | String   | Currently only support "WECHATPAY" , "PRESTO" , "BOOST" , "TNG" , "MAYBANK" , "ALIPAY_CN" , "GRABPAY_MY" | ALL                                        |
| <code>type</code>          | String   | Currently only support "QUICKPAY"                                                                        | "QUICKPAY"                                 |
| <code>status</code>        | String   | Status returned from WeChat server                                                                       | "SUCCESS"                                  |
| <code>error</code>         | String   | (Refer `Appendix: Error Codes`)                                                                          | {}                                         |
| <code>createdAt</code>     | DateTime | Creation date time of transaction                                                                        | "2018-03-21T06:41:22Z"                     |
| <code>updatedAt</code>     | DateTime | Last update date time of transaction                                                                     | "2018-03-21T06:41:22Z"                     |

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

<strong>Order object (`"order"`):</strong>

| Parameter                   | Type   | Description                                      | Example                        |
| --------------------------- | ------ | ------------------------------------------------ | ------------------------------ |
| <code>id</code>             | String | Order ID (from Merchant), max: 24                | "134850717797247290"           |
| <code>title</code>          | String | Order title, max: 32                             | "Sales"                        |
| <code>details</code>        | String | Order details, max: 600                          | "1 x iPhone X; 2 x SAMSUNG S8" |
| <code>additionalData</code> | String | For merchant's remark, max 128                   | ""                             |
| <code>currencyType</code>   | String | Currency notation (currently only support `MYR`) | "MYR"                          |
| <code>amount</code>         | Uint   | Amount of order in cent                          | 100                            |
