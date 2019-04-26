#Merchant

This is the section describing how to query merchant details.

- Restricted to scope: `get_merchant_profile`
- Authentication: Access token obtained from [Generate Access Token](https://doc.revenuemonster.my/#66368026-71ee-4640-8ad7-208f843c6d6c) into `Authorization` header value as `Bearer [access_token]`.

<!---=================================--->
<!---Get Merchant Profile --->
<!---=================================--->

##Get Merchant Profile 
**Method <span style="color:Green" , bold >`GET`</span>**

<code>https://sb-open.revenuemonster.my/v3/merchant</code>

To query for merchant details.

***REQUEST***

<strong>Request Parameters:</strong>

*Note: No request parameter is required for this endpoint*

Eg. Plain text parameters:
`method=get&nonceStr=VYNknZohxwicZMaWbNdBKUrnrxDtaRhN&requestUrl=https://sb-open.revenuemonster.my/v3/merchant&signType=sha256&timestamp=1527407052`

>Example Request 

```json
curl --location --request GET "https://sb-open.revenuemonster.my/v3/merchant" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 JyMp21esWHb8r+wxpsj2J++6TGaO+pSfHsjqmG2T+S59e+S3sxsr+/cJHbmC3CaenBwb1Cp3/4EJxhzXWf7OEg==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1527407052" \
  --data "{

}"
```


***RESPONSE***

<strong>Response Parameters:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>item</code> | Object | Object of refund details. | (Refer explanantion below)
<code>code</code> | String | Status returned from Revenue Monster server, whether successfully called our endpoint or not. | "SUCCESS"

>Example Respond

```json
{
  "item": {
    "id": "5611759774758429587",
    "companyName": "YUSSUF TEST",
    "companyType": "SOLE PROPRIETORSHIP",
    "companyLogoUrl": "https://storage.googleapis.com/rm-dev-merchant/5611759774758429587/logo/merchant.jpeg",
    "registrationNumber": "12343",
    "businessCategory": "INSURANCE SERVICES",
    "establishedAt": "2018-05-12T16:00:00Z",
    "countryCode": "60",
    "phoneNumber": "167367171",
    "addressLine1": "20, JALAN JASA 38, TAMAN MUTIARA RINI",
    "addressLine2": "",
    "postcode": "81300",
    "city": "AYER HITAM",
    "state": "JOHOR",
    "country": "MALAYSIA",
    "invoiceAddress": {
      "addressLine1": "20, JALAN JASA 38, TAMAN MUTIARA RINI",
      "addressLine2": "",
      "postcode": "81300",
      "city": "AYER HITAM",
      "state": "JOHOR",
      "country": "MALAYSIA"
    },
    "isActive": true,
    "status": "VERIFIED",
    "isMasterMerchant": false,
    "masterMerchantId": "2301663653361832803",
    "isPartner": false,
    "partnerId": "2301663653361832803",
    "gstNo": "",
    "createdAt": "2018-05-14T09:26:22Z",
    "updatedAt": "2018-05-22T05:23:02Z"
  },
  "code": "SUCCESS"
}
```

<strong>Item Object:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>id</code> | String | Store ID | "6170506694335521334"
<code>companyName</code> | String | Company name of merchant | "REVENUE MONSTER"
<code>companyType</code> | String | Type of company incorporation | "SOLE PROPRIETOR"
<code>companyLogoUrl</code> | String | Public URL to show merchant's logo | "https://storage.googleapis.com/rm-dev-asset/img/merchant.png"
<code>registrationNumber</code> | String | Registration number of merchant  | “12344”
<code>businessCategory</code> | String | Business category of merchant | "SOFTWARE AND IT"
<code>establishedAt</code> | String | Established date time of merchant | "2018-03-26T04:50:57Z"
<code>countryCode</code> | String | Country code of merchant contact number | "60"
<code>phoneNumber</code> | String | Phone number of merchant | "377334080"
<code>addressLine1</code> | String | Address 1 of merchant | "20, JALAN JASA 38, TAMAN MUTIARA RINI"
<code>addressLine2</code> | String | Address 2 of merchant | ""
<code>postcode</code> | String | Postcode of merchant | “81300”
<code>city</code> | String | City of merchant | "Selangor"
<code>state</code> | String | State of merchant | "Selangor"
<code>country</code> | String | Country of merchant | "Malaysia"
<code>invoiceAddres</code> | Object | Object of Invoice Address | (Refer below)
<code>isActive</code> | Boolean | Merchant active or deactivated status | true
<code>status</code> | String | Current status of merchant | “REVIEWING”
<code>isMasterMerchant</code> | Bool | Master Merchant flag | true
<code>masterMerchantId</code> | String | Master Merchant ID, if any | "2301663653361832803"
<code>isPartner</code> | Bool | Partner Merchant flag | true
<code>partnerId</code> | String | Partner Merchant ID, if any | "2301663653361832803"
<code>gstNo</code> | String | GST No, if any | ""
<code>createdAt</code> | DateTime | Creation date time of merchant | "2018-02-12T08:53:13Z"
<code>updatedAt</code> | DateTime | Last update date time of merchant | "2018-02-12T08:53:13Z"

<strong>Invoice Address Object:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>addressLine1</code> | String | Address 1 of merchant | "20, JALAN JASA 38, TAMAN MUTIARA RINI"
<code>addressLine2</code> | String | Address 2 of merchant | ""
<code>postcode</code> | String | Postcode of merchant | “81300”
<code>city</code> | String | City of merchant | "Selangor"
<code>state</code> | String | State of merchant | "Selangor"
<code>country</code> | String | Country of merchant | "Malaysia"

<!---=================================--->
<!---Get Merchant Subscriptions--->
<!---=================================--->

##Get Merchant Subscriptions   
**Method <span style="color:Green" , bold >`Get`</span>** 

<code>https://sb-open.revenuemonster.my/v3/merchant/subscriptions</code>


To query for merchant product subscription details.

>Example Request

```json
curl --location --request GET "https://sb-open.revenuemonster.my/v3/merchant/subscriptions" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 fvPpcLVgEcEFWc9sZkOxDFENrXcBodygcHp3XPTiN8BPs2IDeCGvYI9ijREeWKaPPenuAcpIGGAf2/xeaHxjMQ==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1527407052" \
  --data "{

}"
```

***REQUEST***

<strong>Request Parameters:</strong>

*Note: No request parameter is required for this endpoint*

Eg. Plain Text Parameters:
`method=get&nonceStr=VYNknZohxwicZMaWbNdBKUrnrxDtaRhN&requestUrl=https://sb-open.revenuemonster.my/v3/merchant&signType=sha256&timestamp=1527407052`

>Example Respond 

```json
{
  "item": [
    {
      "id": 1001,
      "gracePeriod": 90,
      "expiryAt": "2018-04-28T06:36:08Z",
      "terminateAt": "2018-07-27T23:59:59Z",
      "status": "ACTIVE"
    },
    {
      "id": 1000,
      "gracePeriod": 90,
      "expiryAt": "2018-04-25T02:51:10Z",
      "terminateAt": "2018-07-24T23:59:59Z",
      "status": "ACTIVE"
    },
    {
      "id": 1003,
      "gracePeriod": 90,
      "expiryAt": "2018-04-29T05:04:30Z",
      "terminateAt": "2018-07-28T23:59:59Z",
      "status": "ACTIVE"
    }
  ],
  "code": "SUCCESS"
}
```
***RESPONSE***

<strong>Response Parameters:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>item</code> | Object | Object of refund details. | (Refer explanantion below)
<code>code</code> | String | Status returned from Revenue Monster server, whether successfully called our endpoint or not. | "SUCCESS"

<strong>Item Object:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>id</code> | String | Store ID | "6170506694335521334"
<code>companyName</code> | String | Company name of merchant | "REVENUE MONSTER"
<code>companyType</code> | String | Type of company incorporation | "SOLE PROPRIETOR"
<code>companyLogoUrl</code> | String | Public URL to show merchant's logo | "https://storage.googleapis.com/rm-dev-asset/img/merchant.png"
<code>registrationNumber</code> | String | Registration number of merchant  | “12344”
<code>businessCategory</code> | String | Business category of merchant | "SOFTWARE AND IT"
<code>establishedAt</code> | String | Established date time of merchant | "2018-03-26T04:50:57Z"
<code>countryCode</code> | String | Country code of merchant contact number | "60"
<code>phoneNumber</code> | String | Phone number of merchant | "377334080"
<code>addressLine1</code> | String | Address 1 of merchant | "20, JALAN JASA 38, TAMAN MUTIARA RINI"
<code>addressLine2</code> | String | Address 2 of merchant | ""
<code>postcode</code> | String | Postcode of merchant | “81300”
<code>city</code> | String | City of merchant | "Selangor"
<code>state</code> | String | State of merchant | "Selangor"
<code>country</code> | String | Country of merchant | "Malaysia"
<code>invoiceAddres</code> | Object | Object of Invoice Address | (Refer below)
<code>isActive</code> | Boolean | Merchant active or deactivated status | true
<code>status</code> | String | Current status of merchant | “REVIEWING”
<code>isMasterMerchant</code> | Bool | Master Merchant flag | true
<code>masterMerchantId</code> | String | Master Merchant ID, if any | "2301663653361832803"
<code>isPartner</code> | Bool | Partner Merchant flag | true
<code>partnerId</code> | String | Partner Merchant ID, if any | "2301663653361832803"
<code>gstNo</code> | String | GST No, if any | ""
<code>createdAt</code> | DateTime | Creation date time of merchant | "2018-02-12T08:53:13Z"
<code>updatedAt</code> | DateTime | Last update date time of merchant | "2018-02-12T08:53:13Z"

<strong>Invoice Address Object:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>addressLine1</code> | String | Address 1 of merchant | "20, JALAN JASA 38, TAMAN MUTIARA RINI"
<code>addressLine2</code> | String | Address 2 of merchant | ""
<code>postcode</code> | String | Postcode of merchant | “81300”
<code>city</code> | String | City of merchant | "Selangor"
<code>state</code> | String | State of merchant | "Selangor"
<code>country</code> | String | Country of merchant | "Malaysia"