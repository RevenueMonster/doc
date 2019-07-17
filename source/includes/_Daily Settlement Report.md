##Daily Settlement Report  
**Method <span style="color:Orange" , bold >`Post`</span>**

`https://sb-open.revenuemonster.my/v3/payment/settlement/csv`

To query for payment transaction using ID.

> Example Request

```json
curl --location --request POST "https://sb-open.revenuemonster.my/v3/payment/settlement/csv" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 OsjlEWZLKx0IXgC5PUk6sM+ZZdrS/ELBNdEGj+okOhVAwo/i+GK91CwEmIbLko+p0Vbs8Ph+iBQG/3DyS7kHug==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1527407052" \
  --data "{
    \"date\": \"2018-08-05\",
    \"method\": \"WECHATPAY\",
    \"region\": \"MALAYSIA\",
    \"sequence\": 1
}"
```

**_REQUEST_**

<strong>Request Parameters:</strong>

| Parameter             | Type   | Required | Description                                                                                           | Example      |
| --------------------- | ------ | -------- | ----------------------------------------------------------------------------------------------------- | ------------ |
| <code>sequence</code> | UInt   | Yes      | Sequence of the report                                                                                | 1            |
| <code>date</code>     | String | Yes      | Date of the report                                                                                    | "2018-08-05" |
| <code>method</code>   | String | Yes      | Currently only support "WECHATPAY" , "PRESTO" , "BOOST" , "TNG" , "MAYBANK" , "Alipay" and "Gradpay". | "ALL"        |
| <code>region</code>   | String | Yes      | Region of wallet, "MALAYSIA" or "CHINA"                                                               | "MALAYSIA"   |

> Example Respond

```json
H,4118165203679668885,REVENUE MONSTER,2018-08-05,1
T,0,0.00,0.00,0.00,0.00,0.00,
S,0,0.00,0.00,0.00,0.00,0.00,
```

**_RESPONSE_**

<strong>Response Parameters:</strong>

| Parameter          | Type   | Description                                                                                               | Example                      |
| ------------------ | ------ | --------------------------------------------------------------------------------------------------------- | ---------------------------- |
| <code>items</code> | Object | Transaction object                                                                                        | (Refer to explanation below) |
| <code>code</code>  | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"                    |

<strong>Transaction object (`"item"`):</strong>

| Parameter                  | Type     | Description                                                                                                                    | Example                                    |
| -------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------ |
| <code>store</code>         | Object   | Store object                                                                                                                   | (Refer to explanation below)               |
| <code>referenceId</code>   | String   | Transaction ID (from WeChat server)                                                                                            | ""                                         |
| <code>transactionId</code> | String   | Transaction ID (from RM server)                                                                                                | "152161448229438994"                       |
| <code>order</code>         | Object   | Order object                                                                                                                   | (Refer to explanation below)               |
| <code>payee</code>         | Object   | Object of userID made payment (payment sender)                                                                                 | {"userId": "o74f0wjjzv9eKRu1fccrZswVFnOQ"} |
| <code>platform</code>      | String   | Currently only support "OPEN_API"                                                                                              | "OPEN_API"                                 |
| <code>method</code>        | String   | Currently only support "WECHATPAY" , "PRESTO" , "BOOST" , "TNG" , "MAYBANK" , "Alipay" and "Gradpay".                          | "ALL"                                      |
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
