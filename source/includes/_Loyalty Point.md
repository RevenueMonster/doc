#Loyalty Point 
To give loyalty points to customers via phone number or member ID

- Scope: `manage_loyalty`
- Authentication: Access token obtained from [Generate Access Token](https://doc.revenuemonster.my/#66368026-71ee-4640-8ad7-208f843c6d6c) into `Authorization` header value as `Bearer [access_token]`.

##Post Give Loyalty Point 
**Method <span style="color:Orange" , bold >`Post`</span>** 

`https://sb-open.revenuemonster.my/v3/loyalty/reward`

To give loyalty points to customers using phone number or member ID.

>Example Request 

```json
curl --location --request POST "https://sb-open.revenuemonster.my/v3/loyalty/reward" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{  
   \"point\": 100,
   \"type\": \"PHONENUMBER\",
   \"countryCode\": \"60\",
   \"phoneNumber\": \"176473298\"
}"
```

***REQUEST***

<strong>Request Parameters:</strong>

Parameter | Type | Required | Description | Example
--------- | ------- | ----------- | --- | ---
<code>point</code> | Integer | Yes | Loyalty point given to customers. | 100
<code>type</code> | String | Yes | "ID" or "PHONENUMBER" | Use phone number or ID to give loyalty points.
<code>memberId</code> | String | No | Member ID if type "ID" being provided. | "2777058682717858418"
<code>countryCode</code> | String | No | Country code if type "PHONENUMBER" being provided. | "60"
<code>phoneNumber</code> | String | No | Phone number if type "PHONENUMBER" being provided. | "172826990"

>Example Respond

```json
{
  "code": "SUCCESS"
}
```

***RESPONSE***

<strong>Response Parameters: </strong>

Parameter | Type | Description | Example
--------- | ------- | :-----------: | ---
<code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer [Appendix 1: Error Codes](https://doc.revenuemonster.my/#da24fa09-5487-49c5-ace7-89944b08162c)) | "SUCCESS"

<h3>Headers</h3>
 | |  
--------- | ------- |
Content-Type | application/json | 
Authorization | Bearer <br>eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1Nywi<br>aXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1<br>lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.<br>dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw |
X-Signature |sha256 <br> Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==  |
X-Nonce-Str | VYNknZohxwicZMaWbNdBKUrnrxDtaRhN | 
X-Timestamp | 1528450585| 

<h3>Body</h3>

<aside> 
<strong>
{  <br>
   "point": 100,<br>
   "type": "ID",<br>
   "memberId": "2777058682717858418"<br>
}
</strong>
</aside>