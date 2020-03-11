#Daily Settlement Report
##Get Payment Reconciliation
**Method <span style="color:Orange" , bold >`Post`</span>**

`https://sb-open.revenuemonster.my/v3/payment/reconciliation`

To Get Daily Payment report

> Example Request

```json
curl --location --request POST "https://sb-open.revenuemonster.my/v3/payment/reconciliation" \
--header "Content-Type: application/json"\
--header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
--header "X-Signature: sha256 OsjlEWZLKx0IXgC5PUk6sM+ZZdrS/ELBNdEGj+okOhVAwo/i+GK91CwEmIbLko+p0Vbs8Ph+iBQG/3DyS7kHug=="\
--header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
--header "X-Timestamp: 1527407052" \
--data-raw "{
	"transactionType": "PAYMENT",
    "date": "2019-12-31",
    "method": [],
    "region": [],
    "cursor": ""
}"
```

**_REQUEST_**

<strong>Request Parameters:</strong>

| Parameter                    | Type   | Required | Description                                | Example      |
| ---------------------------- | ------ | -------- | ------------------------------------------ | ------------ |
| <code>transactionType</code> | String | Yes      | "PAYMENT" or "REFUND"                      | "PAYMENT"    |
| <code>date</code>            | String | Yes      | Date of the report                         | "2019-12-31" |
| <code>method</code>          | String | Yes      | [RM currently supported method](#quickpay) | []           |
| <code>region</code>          | String | Yes      | Region of wallet, "MALAYSIA" or "CHINA"    | []           |
| <code>cursor</code>          | String | Yes      | Optional, if pagination exists             | ""           |

> Example Respond

```json
{
  "items": [
    {
      "transactionAt": "2019-12-31T07:00:10Z",
      "merchantId": "4118165203679668885",
      "merchantName": "Revenue Monster Sdn Bhd",
      "storeId": "4949529109748431621",
      "storeName": "Kim's Food Corner",
      "region": "MALAYSIA",
      "method": "TNG",
      "transactionType": "PAYMENT",
      "type": "QUICK_PAY",
      "transactionId": "191231070009010323431829",
      "orderId": "1577775608765190100M6010",
      "currencyType": "MYR",
      "grossAmount": "0.10",
      "mdr": "0.70",
      "serviceFee": "-0.00",
      "settlementAmount": "0.10"
    },
    {
      "transactionAt": "2019-12-31T07:42:55Z",
      "merchantId": "4118165203679668885",
      "merchantName": "Revenue Monster Sdn Bhd",
      "storeId": "4949529109748431621",
      "storeName": "Kim's Food Corner",
      "region": "MALAYSIA",
      "method": "TNG",
      "transactionType": "PAYMENT",
      "type": "QUICK_PAY",
      "transactionId": "191231074255010324053928",
      "orderId": "1577778173933190100M6010",
      "currencyType": "MYR",
      "grossAmount": "1.00",
      "mdr": "0.70",
      "serviceFee": "-0.01",
      "settlementAmount": "0.99"
    }
  ],
  "code": "SUCCESS",
  "meta": {}
}
```

**_RESPONSE_**

<strong>Response Parameters:</strong>

| Parameter          | Type   | Description                                                                                               | Example                      |
| ------------------ | ------ | --------------------------------------------------------------------------------------------------------- | ---------------------------- |
| <code>items</code> | Object | Transaction object                                                                                        | (Refer to explanation below) |
| <code>code</code>  | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"                    |
| <code>meta</code>  | Object | Database object                                                                                           | {}                           |

<strong>Transaction object (`"item"`):</strong>

| Parameter                     | Type     | Description                                                                    | Example                    |
| ----------------------------- | -------- | ------------------------------------------------------------------------------ | -------------------------- |
| <code>transactionAt</code>    | DateTime | Transaction date time of transaction                                           | "2019-12-31T07:00:10Z"     |
| <code>merchantId</code>       | String   | (Can view From RM Portal)                                                      | "4118165203679668885"      |
| <code>merchantName</code>     | String   | (Can view From RM Portal)                                                      | "Revenue Monster Sdn Bhd"  |
| <code>storeId</code>          | String   | Store ID                                                                       | "4949529109748431621"      |
| <code>storeName</code>        | String   | Store Name                                                                     | "Kim's Food Corner"        |
| <code>region</code>           | String   | Region of wallet, "MALAYSIA" or "CHINA"                                        | "MALAYSIA"                 |
| <code>method</code>           | String   | tyuioigiigqhih                                                                 | "TNG"                      |
| <code>transactionType</code>  | String   | "PAYMENT" or "REFUND"                                                          | "PAYMENT"                  |
| <code>type</code>             | String   | "QUICK_PAY" , "QR_PAY","Web_Payment" , "Mobile_Payment" , "Mobile_Web_Payment" | "QUICK_PAY"                |
| <code>transactionId</code>    | String   | Transaction ID (from RM server)                                                | "191231070009010323431829" |
| <code>orderId</code>          | String   | Order ID (from Merchant), max: 24                                              | "1577775608765190100M6010" |
| <code>currencyType</code>     | String   | Currency notation (currently only support `MYR`)                               | "MYR"                      |
| <code>grossAmount</code>      | Double   | Gross Amount QR pay                                                            | "0.10"                     |
| <code>mdr</code>              | Double   | MDR (from RM server)                                                           | "0.70"                     |
| <code>serviceFee</code>       | Double   | Service Fee (from RM server)                                                   | "-0.00"                    |
| <code>settlementAmount</code> | Double   | Settlement Amount                                                              | "0.10"                     |

| Parameter                  | Type     | Description                                                                                                                    | Example                                    |
| -------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------ |
| <code>store</code>         | Object   | Store object                                                                                                                   | (Refer to explanation below)               |
| <code>referenceId</code>   | String   | Transaction ID (from WeChat server)                                                                                            | ""                                         |
| <code>transactionId</code> | String   | Transaction ID (from RM server)                                                                                                | "152161448229438994"                       |
| <code>order</code>         | Object   | Order object                                                                                                                   | (Refer to explanation below)               |
| <code>payee</code>         | Object   | Object of userID made payment (payment sender)                                                                                 | {"userId": "o74f0wjjzv9eKRu1fccrZswVFnOQ"} |
| <code>platform</code>      | String   | Currently only support "OPEN_API"                                                                                              | "OPEN_API"                                 |
| <code>method</code>        | String   | Currently only support "WECHATPAY" , "PRESTO" , "BOOST" , "TNG" , "MAYBANK" , "ALIPAY" , "GRABPAY".                            | "ALL"                                      |
| <code>type</code>          | String   | Currently only support "QUICKPAY"                                                                                              | "QUICKPAY"                                 |
| <code>status</code>        | String   | Status returned from WeChat server, "SUCCESS" or "IN_PROCESS" or "FAILED". "IN_PROCESS" means user scanned and making payment. | "FAILED"                                   |
| <code>createdAt</code>     | DateTime | Creation date time of transaction                                                                                              | "2018-03-21T06:41:22Z"                     |
| <code>updatedAt</code>     | DateTime | Last update date time of transaction                                                                                           | "2018-03-21T06:41:22Z"                     |

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

<strong>Order object (`"order"`):</strong>

| Parameter                   | Type   | Description                                    | Example                        |
| --------------------------- | ------ | ---------------------------------------------- | ------------------------------ |
| <code>id</code>             | String | Order ID (from Merchant)                       | "134850717797247290"           |
| <code>title</code>          | String | Order title                                    | "Sales"                        |
| <code>details</code>        | String | Order details                                  | "1 x iPhone X; 2 x SAMSUNG S8" |
| <code>additionalData</code> | String | For merchant's remark                          | ""                             |
| <code>currencyType</code>   | String | Currency notation (currently only support MYR) | "MYR"                          |
| <code>amount</code>         | Uint   | Amount of order                                | 100                            |
