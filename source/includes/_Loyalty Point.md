#Loyalty Point
To give loyalty points to customers via phone number or member ID

- Scope: `manage_loyalty`
- Authentication: Access token obtained from [Generate Access Token](https://doc.revenuemonster.my/#66368026-71ee-4640-8ad7-208f843c6d6c) into `Authorization` header value as `Bearer [access_token]`.

##Give Loyalty Point
**Method <span style="color:Orange" , bold >`Post`</span>**

`https://sb-open.revenuemonster.my/v3/loyalty/reward`

To give loyalty points to customers using phone number or member ID.

> Example Request

```json
curl --location --request POST "https://sb-open.revenuemonster.my/v3/loyalty/reward" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{
    \"currencyType\": \"MYR"\,
   \"point\": 100,
   \"type\": \"PHONENUMBER\",
   \"countryCode\": \"60\",
   \"phoneNumber\": \"176473298\"
}"
```

> Example Request

```json
curl --location --request POST "https://sb-open.revenuemonster.my/v3/loyalty/reward" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{

   \"currencyType\": \"MYR\",
   \"point\": 100,
   \"type\": \"QRCODE\",

}"
```

**_REQUEST_**

<strong>Request Parameters:</strong>

| Parameter                 | Type    | Required | Description                                        | Example                                                  |
| ------------------------- | ------- | -------- | -------------------------------------------------- | -------------------------------------------------------- |
| <code>currencyType</code> | String  | Yes      | Currently `MYR` only                               | MYR                                                      |
| <code>point</code>        | Integer | Yes      | Loyalty point given to customers.                  | 100                                                      |
| <code>type</code>         | String  | Yes      | "ID", "PHONENUMBER" or "QRCODE"                    | Use phone number , ID or QR Code to give loyalty points. |
| <code>memberId</code>     | String  | No       | Member ID if type "ID" being provided.             | "2777058682717858418"                                    |
| <code>countryCode</code>  | String  | No       | Country code if type "PHONENUMBER" being provided. | "60"                                                     |
| <code>phoneNumber</code>  | String  | No       | Phone number if type "PHONENUMBER" being provided. | "172826990"                                              |

> Example Respond (PhoneNumber)

```json
{
  "code": "SUCCESS"
}
```

> Example Respond (QRCDOE)

```json
{
  "item": {
    "qrCodeUrl": "https://dev-rm-api.ap.ngrok.io/qr/4118165203679668885/loyalty/d3008719d04cab91c53eb0b5d8cc4ee6"
  },
  "code": "SUCCESS"
}
```

**_RESPONSE_**

<strong>Response Parameters: </strong>

| Parameter         | Type   |                                                                           Description                                                                            | Example   |
| ----------------- | ------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------: | --------- |
| <code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer [Appendix 1: Error Codes](https://doc.revenuemonster.my/#appendix-1-error-codes)) | "SUCCESS" |

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

<!-- Give Spending Loyalty Point -->

##Give Spending Loyalty Point
**Method <span style="color:Orange" , bold >`POST`</span>** <br/>

`https://sb-open.revenuemonster.my/v3/loyalty/spending-reward`

To give loyalty points to customers using phone number or member ID.

> Example Request

```json
curl --location --request POST "{{open_base_path}}/v3/loyalty/reward" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer {{clientToken}}" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{
   \"currencyType\": \"MYR\",
   \"amount\": 100,
   \"type\": \"PHONENUMBER\",
   \"countryCode\": \"60\",
   \"phoneNumber\": \"176473298\"
}"
```

> Example Request (QRCODE)

```json
curl --location --request POST "{{open_base_path}}/v3/loyalty/reward" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer {{clientToken}}" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{
   \"currencyType\": \"MYR\",
   \"amount\": 100,
   \"type\": \"QRCODE\",

}"
```

**_REQUEST_**

<strong>Request Parameters:</strong>

| Parameter                 | Type    | Required | Description                                        | Example                                                  |
| ------------------------- | ------- | -------- | -------------------------------------------------- | -------------------------------------------------------- |
| <code>currencyType</code> | String  | Yes      | Currently `MYR` only                               | MYR                                                      |
| <code>point</code>        | Integer | Yes      | Loyalty point given to customers.                  | 100                                                      |
| <code>type</code>         | String  | Yes      | "ID" ,"PHONENUMBER" or "QRCODE"                    | Use phone number , ID or QR Code to give loyalty points. |
| <code>memberId</code>     | String  | No       | Member ID if type "ID" being provided.             | "2777058682717858418"                                    |
| <code>countryCode</code>  | String  | No       | Country code if type "PHONENUMBER" being provided. | "60"                                                     |
| <code>phoneNumber</code>  | String  | No       | Phone number if type "PHONENUMBER" being provided. | "172826990"                                              |

> Example Respond (Phone Number)

```json
{
  "code": "SUCCESS"
  "item": {
    "id": "d3008719d04cab91c53eb0b5d8cc4ee6"
  }
}
```

> Example Respond (QRCDOE)

```json
{
  "item": {
    "qrCodeUrl": "https://dev-rm-api.ap.ngrok.io/qr/4118165203679668885/loyalty/d3008719d04cab91c53eb0b5d8cc4ee6",
    "id": "d3008719d04cab91c53eb0b5d8cc4ee6"
  },
  "code": "SUCCESS"
}
```

**_RESPONSE_**

<strong>Response Parameters: </strong>

| Parameter         | Type   |                                                                           Description                                                                            | Example   |
| ----------------- | ------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------: | --------- |
| <code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer [Appendix 1: Error Codes](https://doc.revenuemonster.my/#appendix-1-error-codes)) | "SUCCESS" |

<h3>Body</h3>

<aside> 
<strong>
{  <br/>
   "currencyType": "MYR",<br/>
   "amount": 100,<br/>
   "type": "ID",<br/>
   "memberId": "2777058682717858418"<br/>
}
</strong>
</aside>

<!-- Cancel Spending Loyalty Point -->

##Cancel Spending Loyalty Poin
**Method <span style="color:Orange" , bold >`POST`</span>**<br/>

`https://sb-open.revenuemonster.my/v3/loyalty/spending-reward/cancel`

> Example Request

```json
curl --location --request POST "{{open_base_path}}/v3/loyalty/spending-reward/cancel" \
--header "Content-Type: application/json"\
--header "Authorization: Bearer {{clientToken}}" \
--header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
--header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
--header "X-Timestamp: 1528450585"\
--data-raw "{
  "id":"dee13d3470f2dd43466c252cfc67f967"

}"
```

**To cancel loyalty points by id**

**_REQUEST_**

**Request Parameters:**

| Parameter | Type   | Required | Description                                    | Example                            |
| --------- | ------ | -------- | ---------------------------------------------- | ---------------------------------- |
| `id`      | String | Yes      | Get the **id** from spending loyalty point api | "dee13d3470f2dd43466c252cfc67f967" |

> Example Respond

```json
{
  "code": "SUCCESS"
}
```

**_RESPONSE_**

<strong>Response Parameters: </strong>

| Parameter         | Type   |                                                                           Description                                                                            | Example   |
| ----------------- | ------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------: | --------- |
| <code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer [Appendix 1: Error Codes](https://doc.revenuemonster.my/#appendix-1-error-codes)) | "SUCCESS" |

<!-- Calculate Spending Reward  -->

##Calculate Spending Reward
**Method <span style="color:Green" , bold >`GET`</span>**

`https://sb-open.revenuemonster.my/v3/loyalty/spending-reward/calculate`

> Example Request

```json
curl --location --request GET "{{open_base_path}}/v3/loyalty/spending-reward/calculate" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer {{clientToken}}" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{
    \"currencyType\": \"MYR\"
	\"amount\": 300
}"
```

**_REQUEST_**

**Request Parameters:**

| Parameter      | Type   | Description          | Example |
| -------------- | ------ | -------------------- | ------- |
| `currencyType` | String | Currently `MYR` only | MYR     |
| `amount`       | int    | Amount Sales         | 300     |

> Example Respond

```json
{
  "item": {
    "point": 300
  },
  "code": "SUCCESS"
}
```

**_RESPONSE_**

<strong>Response Parameters: </strong>

| Parameter | Type   | Description                                                                                                                                                      | Example                      |
| --------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------- |
| `item`    | Object | Point object                                                                                                                                                     | (Refer to explanation below) |
| `code`    | String | Successfully call this endpoint. If fail, will return error code object (Refer [Appendix 1: Error Codes](https://doc.revenuemonster.my/#appendix-1-error-codes)) | "SUCCESS"                    |

<strong>Point Object (`item`)</strong> <br/>

| Parameter | Type | Description                       | Example |
| --------- | ---- | --------------------------------- | ------- |
| `Point`   | int  | Loyalty point given to customers. | 300     |

Currency notation (currently only support MYR)
