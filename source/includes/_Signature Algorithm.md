#Signature Algorithm

**Signature algorithm is used to sign your payment API request with a private key to obtain additional security.**


Example: 

**<span style="color:Orange" , bold >`PATCH`</span>** Update Store



**Step 1: Prepare Request Parameters**

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
<code>geoLocation</code> | Object of [String] | No | Geo Location (latitude and longtitude) of store | {"Lat": 3.1349857, "Lng": 101.6136659 }

**Step 2: Sort by order**

<aside class="success"> <strong>Example :</strong>
<br>
<strong>
{ <br>
  "addressLine1": "gugusan melur", <br>
    "city": "petaling jaya", <br>
    "country": "malaysia.", <br>
    "countryCode": "60", <br>
    "name": "yussuf", <br>
    "phoneNumber": "176473298", <br>
    "postCode": "47810", <br>
    "state": "selangor" <br />
}
</strong>
</aside>

**Step 3: Encode the data in Step 2 using Base64 format.**

**Example :**
<br />
`eyJjdXJyZW5jeVR5cGUiOiJNWVIiLCJvdXRUcmFkZU5vIjoiMTgwNjA2MDYxMjU5NTUzNzg1MTMzOSIsInJlYXNvbiI6ImhlbGxvIiwicmVmdW5kIjp7ImFtb3VudCI6MTAsInR5cGUiOiJGVUxMIn0sInRvdGFsQW1vdW50IjoxMH0`


**Step 4: Construct plain text parameters:**

<strong>Plain Text Parameters:</strong>

Parameter | Type | Required | Description | Example
--------- | ------- | ----------- | --- | ---
<code>data</code> | String | Yes | Base64 data body from Step 3. | "eyJjdXJyZW5jeVR5cGUiOiJNWVIiLCJvdXRUcmFkZU5vIjoiMTgwNjA2MDYxMjU5NTUzNzg1MTMzOSIsInJlYXNvbiI6ImhlbGxvIiwicmVmdW5kIjp7ImFtb3VudCI6MTAsInR5cGUiOiJGVUxMIn0sInRvdGFsQW1vdW50IjoxMH0"
<code>method</code> | String | Yes | HTTP call method used. | "patch"
<code>nonceStr</code> | String | Yes | Random string | "VYNknZohxwicZMaWbNdBKUrnrxDtaRhN"
<code>requestURl</code> | String | Yes | Request URL must be exactly the same, together with URI. | https://sb-open.revenuemonster.my/v3/store/1662168764176583360
<code>signType</code> | String | Yes | Sign Type, prefer SHA-256 | "sha256"
<code>timestamp</code> | String | Yes | UNIX timestamp of request | "1527407052"

**Example : Combine All In One Line**

<br/>
`data=eyJjdXJyZW5jeVR5cGUiOiJNWVIiLCJvdXRUcmFkZU5vIjoiMTgwNjA2MDYxMjU5NTUzNzg1MTMzOSIsInJlYXNvbiI6ImhlbGxvIiwicmVmdW5kIjp7ImFtb3VudCI6MTAsInR5cGUiOiJGVUxMIn0sInRvdGFsQW1vdW50IjoxMH0=&method=patch&nonceStr=VYNknZohxwicZMaWbNdBKUrnrxDtaRhN&requestUrl=https://sb-open.revenuemonster.my/v3/store/1662168764176583360&signType=sha256&timestamp=1527407052`

 
**Step 5: Sign with CLIENT PRIVATE KEY**

<strong>Signature of Request Data:</strong>

Parameter | Type | Required | Description | Example
--------- | ------- | ----------- | --- | ---
<code>data</code> | String | Yes | Signature of request data in *Step 1* using **CLIENT PRIVATE KEY** | (Refer below), `[sign method] [signature]`

**Example`Signature of Request Data`:**

<br/>
`sha256 IrBg6t73VsH7ieEnQDB4CXHFjMWUkp8Dtddpxqw+4Gvz6Tag7Dx6nrfAt2ofYK8xZN9aBCvAKAfmAOGWIXnsTXfhFBnMA2kadiga7ufUJ81ozyhllbiliRM2ugw1OcqSTLRHWBPhrVwhHBxgDiG9wbuI3FKURrz+CufYYakFoCw=`

```json
curl --request PATCH \
  --url 'https://sb-open.revenuemonster.my/store/1662168764176583360' \
  --header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw' \
  --header 'Content-Type: application/json' \
  --header 'X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN' \
  --header 'X-Signature: sha256 IrBg6t73VsH7ieEnQDB4CXHFjMWUkp8Dtddpxqw+4Gvz6Tag7Dx6nrfAt2ofYK8xZN9aBCvAKAfmAOGWIXnsTXfhFBnMA2kadiga7ufUJ81ozyhllbiliRM2ugw1OcqSTLRHWBPhrVwhHBxgDiG9wbuI3FKURrz+CufYYakFoCw=' \
  --header 'X-Timestamp: 1527407052' \
  --data '{
  "addressLine1": "gugusan melur",
    "city": "petaling jaya",
    "country": "malaysia.",
    "name": "yussuf",
    "countryCode": "60",
    "phoneNumber": "176473298",
    "postCode": "47810",
    "state": "selangor"
}'
```

**Step 6: Put this `Signature of Request Data` into header under X-Signature, construct the request as below and call API endpoint:**




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
<code>geoLocation</code> | Object of [String] | Geo Location (latitude and longtitude) of store | {"Lat": 3.1349857, "Lng": 101.6136659 }
<code>status</code> | String | Current status of store | "ACTIVE"
<code>isDefault</code> | String | Default store of merchant (first store created upon signup) | true
<code>createdAt</code> | DateTime | Creation date time of store | "2018-02-12T08:53:13Z"
<code>updatedAt</code> | DateTime | Last update date time of store | "2018-02-12T08:53:13Z"