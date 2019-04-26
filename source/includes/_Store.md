#Store 
This is the section describing how to manage merchant stores(outlets).

- Restricted to scope: `manage_store`
- Authentication: Access token obtained from [Generate Access Token](https://doc.revenuemonster.my/#66368026-71ee-4640-8ad7-208f843c6d6c) into `Authorization` header value as `Bearer [access_token]`.

<!--==================--->
<!--Get Store--->
<!--==================--->

##Get Store
**Method <span style="color:Green" , bold >`Get`</span>** 

<code>https://sb-open.revenuemonster.my/v3/stores</code>

To query for ALL stores under this merchant.

>Exxample Request 

```json
curl --location --request GET "https://sb-open.revenuemonster.my/v3/stores" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 O5T6ythlvnlr1f8NS0VsMRDSmIPhuZ8cmHmvGaEJz2yA8kdS71h5MpO1L7wCuQPRQ/fMWtziEMdjTQ7dbYbbEw==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1527407052" \
  --data "{

}"
```

***REQUEST***

<strong>Request Parameters:</strong>

*Note: No request parameter is required for this endpoint*

Eg. Plain Text Parameters:

`method=get&nonceStr=VYNknZohxwicZMaWbNdBKUrnrxDtaRhN&requestUrl=https://sb-open.revenuemonster.my/v3/stores&signType=sha256&timestamp=1527407052`


>Example Respond 

```json
{
  "items": [
    {
      "id": "1662168764176583360",
      "name": "Test Store",
      "addressLine1": "20, JALAN JASA 38, TAMAN MUTIARA RINI",
      "addressLine2": "",
      "postCode": "81230",
      "city": "BALING",
      "state": "KEDAH",
      "country": "MALAYSIA",
      "countryCode": "60",
      "phoneNumber": "12354645547",
      "geoLocation": {
        "latitude": 0,
        "longitude": 0
      },
      "status": "ACTIVE",
      "createdAt": "2018-05-16T08:05:02Z",
      "updatedAt": "2018-05-16T08:05:02Z"
    },
    {
      "id": "526742853846521323",
      "name": "yussuf",
      "addressLine1": "GUGUSAN MELUR",
      "addressLine2": "",
      "postCode": "47810",
      "city": "PETALING JAYA",
      "state": "SELANGOR",
      "country": "MALAYSIA.",
      "countryCode": "60",
      "phoneNumber": "176473298",
      "geoLocation": {
        "latitude": 0,
        "longitude": 0
      },
      "status": "ACTIVE",
      "createdAt": "2018-05-27T10:12:25Z",
      "updatedAt": "2018-05-27T10:12:25Z"
    },
    {
      "id": "6883264812332703106",
      "name": "XXX",
      "addressLine1": "",
      "addressLine2": "",
      "postCode": "",
      "city": "",
      "state": "",
      "country": "",
      "countryCode": "",
      "phoneNumber": "",
      "geoLocation": {
        "latitude": 0,
        "longitude": 0
      },
      "status": "ACTIVE",
      "createdAt": "2018-05-14T09:26:23Z",
      "updatedAt": "2018-05-14T09:26:23Z"
    }
  ],
  "code": "SUCCESS",
  "meta": {
    "count": 3,
    "total": 3
  }
}
```

***RESPONSE***

<strong>Response Parameters:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>items</code> | Object[] | Array of store object | (Refer to explanation below)
<code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"
<code>meta</code> | Object | Database object | (Refer to explanation below)

<strong>Array of store object (`"items"`):</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>id</code> | String | Store ID | "6170506694335521334"
<code>name</code> | String | Store Name | "REVENUE MONSTER"
<code>addressLine1</code> | String | Store Address 1 | "B-5-30, 5th Floor, Block Bougainvillea,"
<code>addressLine2</code> | String | Store Address 2 | "PJU 6A, Lebuhraya SPRINT, 10 Boulevard,"
<code>postCode</code> | String | Postcode of store | "47400"
<code>city</code> | String | City of store | "Petaling Jaya"
<code>state</code> | String | State of store | "Selangor"
<code>country</code> | String | Country of store | "Malaysia"
<code>countryCode</code> | String | Country code of store contact number | "60"
<code>phoneNumber</code> | String | Phone number of store | "377334080"
<code>geoLocation</code> | Object of [String] | Geo Location (latitude and longtitude) of store | {"Lat": 3.1349857, "Lng": 101.6136659 }
<code>status</code> | String | Current status of store | "ACTIVE"
<code>isDefault</code> | String | Default store of merchant (first store created upon signup) | true
<code>createdAt</code> | DateTime | Creation date time of store | "2018-02-12T08:53:13Z"
<code>updatedAt</code> | DateTime | Last update date time of store | "2018-02-12T08:53:13Z"


<strong>Database object (`"meta"`):</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>count</code> | Int | Current page record | 1
<code>total</code> | Int | Total record in database | 1
<code>cursor</code> | String | Optional, if pagination exists. | 1

- *Note: To pass in pagination cursor, you may use query string: ~/?cursor= < cursor >*


<!--==================--->
<!--Get Store By ID--->
<!--==================--->

##Get Store By ID 

<code>https://sb-open.revenuemonster.my/v3/store/10946114768247530</code>

<h3>REQUEST</h3>

**Request Parameters:**

Eg.Plain Text Parameters:

<code>method=get&nonceStr=MNhrdDgIDlTKdlYXzfhEvqHpGjRhvrPe&requestUrl=https://sb-open.revenuemonster.my/v3/store/1553067214325776225&
signType=sha256&timestamp=1527407052</code>


>Example Request

```json
curl --location --request GET "https://sb-open.revenuemonster.my/v3/store/10946114768247530" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 O5T6ythlvnlr1f8NS0VsMRDSmIPhuZ8cmHmvGaEJz2yA8kdS71h5MpO1L7wCuQPRQ/fMWtziEMdjTQ7dbYbbEw==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1527407052" \
  --data "{

}"
```
<h3>Response</h3>

**Response Parameters:**

>Example Respond

```json
{
    "item": {
        "id": "1553067214325776225",
        "name": "Starbucks",
        "imageUrl": "https://storage.googleapis.com/rm-prod-asset/img/store.png",
        "addressLine1": "Berjaya Times Square,  Imbi",
        "addressLine2": "",
        "postCode": "55100",
        "city": "Kuala Lumpur",
        "state": "W.P. Kuala Lumpur",
        "country": "Malaysia",
        "countryCode": "60",
        "phoneNumber": "1234567890",
        "geoLocation": {
            "latitude": 3.1421984,
            "longitude": 101.71055120000005
        },
        "status": "ACTIVE",
        "createdAt": "2019-03-20T07:33:34Z",
        "updatedAt": "2019-03-20T07:33:34Z"
    },
    "code": "SUCCESS"
}
```

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>items</code> | Object[] | Array of store object | (Refer to explanation below)
<code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"


<strong>Array of store object (`"items"`):</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>id</code> | String | Store ID | "6170506694335521334"
<code>name</code> | String | Store Name | "REVENUE MONSTER"
<code>imageUrl</code> | String | Image of your Store | "https://storage.googleapis.com/rm-prod-asset/img/store.png"
<code>addressLine1</code> | String | Store Address 1 | "B-5-30, 5th Floor, Block Bougainvillea,"
<code>addressLine2</code> | String | Store Address 2 | "PJU 6A, Lebuhraya SPRINT, 10 Boulevard,"
<code>postCode</code> | String | Postcode of store | "55100"
<code>city</code> | String | City of store | "Petaling Jaya"
<code>state</code> | String | State of store | "Selangor"
<code>country</code> | String | Country of store | "Malaysia"
<code>countryCode</code> | String | Country code of store contact number | "60"
<code>phoneNumber</code> | String | Phone number of store | "377334080"
<code>geoLocation</code> | Object of [String] | Geo Location (latitude and longtitude) of store | {"Lat": 3.1349857, "Lng": 101.6136659 }
<code>status</code> | String | Current status of store | "ACTIVE"
<code>createdAt</code> | DateTime | Creation date time of store | "2018-02-12T08:53:13Z"
<code>updatedAt</code> | DateTime | Last update date time of store | "2018-02-12T08:53:13Z"



<!--=============--->
<!--create Store--->
<!--=============--->

##Create Store
**Method <span style="color:Orange" , bold >`Post`</span>** 

<code>https://sb-open.revenuemonster.my/v3/store</code>

To create store under this merchant.

***REQUEST***

<strong>Request Parameters:</strong>

Parameter | Type | Required | Description | Example
--------- | ------- | ----------- | --- | ---
<code>name</code> | String | Yes | Store Name | "REVENUE MONSTER"
<code>addressLine1</code> | String | Yes | Store Address 1 | "B-5-30, 5th Floor, Block Bougainvillea,"
<code>addressLine2</code> | String | No | Store Address 2 | "PJU 6A, Lebuhraya SPRINT, 10 Boulevard,"
<code>postCode</code> | String | Yes | Postcode of store | "47400"
<code>city</code> | String | Yes | City of store | "Petaling Jaya"
<code>state</code> | String | Yes | State of store  | "Selangor"
<code>country</code> | String | Yes | Country of store | "Malaysia"
<code>countryCode</code> | String | Yes | Country code of store contact number | "60"
<code>phoneNumber</code> | String | Yes | Phone number of store | "377334080"
<code>geoLocation</code> | Object of [Float] | No | Geo Location (latitude and longtitude) of store | {"latitude": 3.1349857, "longitude": 101.6136659 }

>Example Request

```json
curl --location --request POST "https://sb-open.revenuemonster.my/v3/store" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 X+IAMfyCdGTE4Or/jdYqBbwRvCpzNqv1lnaXUd+iWE37nCmxAT69x3PqdmcwyQnmO6BuHsqNy7znCFg3L9sjxg==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1527407052" \
  --data "{
	\"addressLine1\": \"gugusan melur\",
    \"city\": \"petaling jaya\",
    \"country\": \"malaysia.\",
    \"name\": \"yussuf\",
    \"countryCode\": \"60\",
    \"phoneNumber\": \"176473298\",
    \"postCode\": \"47810\",
    \"state\": \"selangor\"
}"
```

***RESPONSE***

<strong>Request Parameters:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>items</code> | Object[] | Array of store object | (Refer to explanation below)
<code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"

>Example Respond

```json
{
  "item": {
    "id": "5237968049713769466",
    "name": "yussuf",
    "addressLine1": "GUGUSAN MELUR",
    "addressLine2": "",
    "postCode": "47810",
    "city": "PETALING JAYA",
    "state": "SELANGOR",
    "country": "MALAYSIA.",
    "countryCode": "60",
    "phoneNumber": "176473298",
    "geoLocation": {
      "latitude": 0,
      "longitude": 0
    },
    "status": "ACTIVE",
    "createdAt": "2018-05-27T17:17:12.196274Z",
    "updatedAt": "2018-05-27T17:17:12.196283Z"
  },
  "code": "SUCCESS"
}
```

<strong>Array of store object (`"items"`):</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>id</code> | String | Store ID | "6170506694335521334"
<code>name</code> | String | Store Name | "REVENUE MONSTER"
<code>addressLine1</code> | String | Store Address 1 | "B-5-30, 5th Floor, Block Bougainvillea,"
<code>addressLine2</code> | String | Store Address 2 | "PJU 6A, Lebuhraya SPRINT, 10 Boulevard,"
<code>postCode</code> | String | Postcode of store | "47400"
<code>city</code> | String | City of store | "Petaling Jaya"
<code>state</code> | String | State of store | "Selangor"
<code>country</code> | String | Country of store | "Malaysia"
<code>countryCode</code> | String | Country code of store contact number | "60"
<code>phoneNumber</code> | String | Phone number of store | "377334080"
<code>geoLocation</code> | Object of [Float] | Geo Location (latitude and longtitude) of store | {"latitude": 3.1349857, "longtitude": 101.6136659 }
<code>status</code> | String | Current status of store | "ACTIVE"
<code>isDefault</code> | String | Default store of merchant (first store created upon signup) | true
<code>createdAt</code> | DateTime | Creation date time of store | "2018-02-12T08:53:13Z"
<code>updatedAt</code> | DateTime | Last update date time of store | "2018-02-12T08:53:13Z"

<!--==================--->
<!--Update Store--->
<!--==================--->

##Update Store
**Method <span style="color:Gray" , bold >`PATC`</span>** 

<code>https://sb-open.revenuemonster.my/v3/store/1662168764176583360</code>

To update specific store under this merchant. Specify `store_id` in query parameter.

>Example Request

```json
curl --location --request PATCH "https://sb-open.revenuemonster.my/v3/store/1662168764176583360" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Uf8oEHcq3l5ZkPc/y9eUsRjoKkx0dLUQz5PEFntWUZcR4A0DYdtQ9+VTx5Rq4e4XsRVp+4KZb4cwpDfzPABCZA==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1527407052" \
  --data "{
	\"addressLine1\": \"gugusan melur\",
    \"city\": \"petaling jaya\",
    \"country\": \"malaysia.\",
    \"name\": \"yussuf\",
    \"countryCode\": \"60\",
    \"phoneNumber\": \"176473298\",
    \"postCode\": \"47810\",
    \"state\": \"selangor\"
}"
```

***REQUEST***

<strong>Request Parameters:</strong>

Parameter | Type | Required | Description | Example
--------- | ------- | ----------- | --- | ---
<code>name</code> | String | Yes | Store Name | "REVENUE MONSTER"
<code>addressLine1</code> | String | Yes | Store Address 1 | "B-5-30, 5th Floor, Block Bougainvillea,"
<code>addressLine2</code> | String | No | Store Address 2 | "PJU 6A, Lebuhraya SPRINT, 10 Boulevard,"
<code>postCode</code> | String | Yes | Postcode of store | "47400"
<code>city</code> | String | Yes | City of store | "Petaling Jaya"
<code>state</code> | String | Yes | State of store  | "Selangor"
<code>country</code> | String | Yes | Country of store | "Malaysia"
<code>countryCode</code> | String | Yes | Country code of store contact number | "60"
<code>phoneNumber</code> | String | Yes | Phone number of store | "377334080"
<code>geoLocation</code> | Object of [Float] | No | Geo Location (latitude and longtitude) of store | {"latitude": 3.1349857, "longtitude": 101.6136659 }

Eg. Plain Text Parameters:<br>
`data=eyJjdXJyZW5jeVR5cGUiOiJNWVIiLCJvdXRUcmFkZU5vIjoiMTgwNjA2MDYxMjU5NTUzNzg1MTMzOSIsInJlYXNvbiI6ImhlbGxvIiwicmVmdW5kIjp7ImFtb3VudCI6MTAsInR5cGUiOiJGVUxMIn0sInRvdGFsQW1vdW50IjoxMH0=&method=patch&nonceStr=VYNknZohxwicZMaWbNdBKUrnrxDtaRhN&requestUrl=https://sb-open.revenuemonster.my/v3/store/1662168764176583360&signType=sha256&timestamp=1527407052`


>Example Respond

```json
{
  "item": {
    "id": "1662168764176583360",
    "name": "yussuf",
    "addressLine1": "GUGUSAN MELUR",
    "addressLine2": "",
    "postCode": "47810",
    "city": "PETALING JAYA",
    "state": "SELANGOR",
    "country": "MALAYSIA.",
    "countryCode": "60",
    "phoneNumber": "176473298",
    "geoLocation": {
      "latitude": 0,
      "longitude": 0
    },
    "status": "ACTIVE",
    "createdAt": "2018-05-27T17:24:06.501633Z",
    "updatedAt": "2018-05-27T17:24:06.501634Z"
  },
  "code": "SUCCESS"
}
```


***RESPONSE***

<strong>Request Parameters:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>items</code> | Object[] | Array of store object | (Refer to explanation below)
<code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"

<strong>Array of store object (`"items"`):</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>id</code> | String | Store ID | "6170506694335521334"
<code>name</code> | String | Store Name | "REVENUE MONSTER"
<code>addressLine1</code> | String | Store Address 1 | "B-5-30, 5th Floor, Block Bougainvillea,"
<code>addressLine2</code> | String | Store Address 2 | "PJU 6A, Lebuhraya SPRINT, 10 Boulevard,"
<code>postCode</code> | String | Postcode of store | "47400"
<code>city</code> | String | City of store | "Petaling Jaya"
<code>state</code> | String | State of store | "Selangor"
<code>country</code> | String | Country of store | "Malaysia"
<code>countryCode</code> | String | Country code of store contact number | "60"
<code>phoneNumber</code> | String | Phone number of store | "377334080"
<code>geoLocation</code> | Object of [Float] | Geo Location (latitude and longtitude) of store | {"latitude": 3.1349857, "longtitude": 101.6136659 }
<code>status</code> | String | Current status of store | "ACTIVE"
<code>isDefault</code> | String | Default store of merchant (first store created upon signup) | true
<code>createdAt</code> | DateTime | Creation date time of store | "2018-02-12T08:53:13Z"
<code>updatedAt</code> | DateTime | Last update date time of store | "2018-02-12T08:53:13Z"

<!--==================--->
<!--Delete Store--->
<!--==================--->

##Delete Store 
**Method <span style="color:Red" , bold >`DEL`</span>**

<code>https://sb-open.revenuemonster.my/v3/store/1662168764176583360</code>

To delete specific store under this merchant. Specify `store_id` in query parameter.

>Example Request

```json
curl --location --request DELETE "https://sb-open.revenuemonster.my/v3/store/1662168764176583360" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 J5x9KSPQSfL7qMdVaEiDekzbHWgG2UnkIMhvWEWU/2B4uk9OnnCxsallgPJfIPq0eVGmE7cWxPj1t2BuS0mMRg==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1527407052" \
  --data "{

}"
```

***REQUEST***

<strong>Request Parameters:</strong>

*Note: No request parameter is required for this endpoint*

Eg. Plain Text Parameters:

`method=delete&nonceStr=VYNknZohxwicZMaWbNdBKUrnrxDtaRhN&requestUrl=https://sb-open.revenuemonster.my/v3/store/1662168764176583360&signType=sha256&timestamp=1527407052`


>Example Respond

```json
{
  "code": "SUCCESS"
}
```

***RESPONSE***

<strong>Response Parameters:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"


