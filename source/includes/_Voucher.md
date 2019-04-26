#Voucher 
To manage vouchers for the merchant.

- Scope: `manage_loyalty_voucher`
- Authentication: Access token obtained from [Generate Access Token](https://doc.revenuemonster.my/#66368026-71ee-4640-8ad7-208f843c6d6c) into `Authorization` header value as `Bearer [access_token]`.


<!---===================--->
<!---Issue Voucher--->
<!---===================--->

##Post Issue Voucher 
**Method <span style="color:Orange" , bold >`Post`</span>** 

>Example Request 

```json
curl --location --request POST "https://sb-open.revenuemonster.my/v3/voucher-batch/EhQKCE1lcmNoYW50EJXVzd3wraqTORIYCgxWb3VjaGVyQmF0Y2gQkvnGweaB2uQg/issue" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{}"
```

`https://sb-open.revenuemonster.my/v3/voucher-batch/EhQKCE1lcmNoYW50EJXVzd3wraqTORIYCgxWb3VjaGVyQmF0Y2gQkvnGweaB2uQg/issue`

To issue vouchers for customer.

The URL is consist of [base_URL]/v3/voucher-batch/[batchkey]/issue.

[base_URL] is the base URL depending on your environment (Sandbox or production)

[batchkey] can be retrieved by viewing at merchant portal or using endpoint `Get voucher Batches`

***REQUEST***

<strong>Request Parameters:</strong>

Just pass in an empty JSON object

>Example Respond

```json
{
  "item": {
    "code": "NAklEfbVdV",
    "qrUrl": "http://api.local.rm:8080/qr/4118165203679668885/voucher/NAklEfbVdV"
  },
  "code": "SUCCESS"
}
```

***RESPONSE***

<strong>Response Parameters: </strong>

Parameter | Type | Description | Example
--------- | ------- | :-----------: | ---
<code>items</code> | Object | Voucher object | (Refer to explanation below)
<code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"

<strong>Voucher object (`"item"`):</strong>

Parameter | Type | Description | Example
--------- | ------- | :-----------: | :-----:|
<code>code</code> | String | Voucher Code, members can keep this code for future redemption. Same as the qrURL below except this code is not a URL.  | "NAklEfbVdV"
<code>qrUrl</code> | String | QR code for user to scan with Wechat or Facebook to add the voucher into their member account. | "http://api.revenuemonster.my/qr<br>/4118165203679668885/voucher/NAklEfbVdV"


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
   <br>
   <br>
   <br>
}
</strong>
</aside>


<!---===================--->
<!---Post Void Voucher--->
<!---===================--->

##Post Void Voucher 
**Method <span style="color:Orange" , bold >`Post`</span>**

`https://sb-open.revenuemonster.my/v3/voucher/NAklEfbVdV/void`

To void voucher(s) of customer.

>Example Request

```json
curl --location --request POST "https://sb-open.revenuemonster.my/v3/voucher/NAklEfbVdV/void" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{}"
```

The URL is consist of [base_URL]/v3/voucher/[code]/issue.

[base_URL] is the base URL depending on your environment (Sandbox or production)

[code] is the `code` generated from `Issue Voucher` endpoint.

***REQUEST***

<strong>Request Parameters:</strong>

Just pass in an empty JSON object


>Example Respond

```json
{
  "item": {
    "key": "EhQKCE1lcmNoYW50EJXVzd3wraqTORIVCgdWb3VjaGVyGgpOQWtsRWZiVmRW",
    "label": "oijfge",
    "redemptionRuleKey": null,
    "voucherBatchKey": "EhQKCE1lcmNoYW50EJXVzd3wraqTORIYCgxWb3VjaGVyQmF0Y2gQkvnGweaB2uQg",
    "type": "GIFT",
    "amount": 0,
    "discountRate": 0,
    "minimumSpendAmount": 0,
    "origin": "SYSTEM",
    "imageUrl": "",
    "memberProfile": null,
    "redemptionRule": null,
    "assignedAt": "2018-09-28T17:15:17Z",
    "payload": null,
    "qrUrl": "",
    "code": "NAklEfbVdV",
    "isShipping": false,
    "address": null,
    "expiry": {
      "type": "DYNAMIC",
      "day": 100,
      "expiredAt": "2019-01-06T17:19:35Z"
    },
    "usedAt": "2018-09-28T17:19:44.686549737Z",
    "redeemedAt": "2018-09-28T17:19:35Z",
    "isDeviceRedeem": false,
    "status": "VOID",
    "createdAt": "2018-06-21T11:08:00Z",
    "updatedAt": "2018-09-28T17:19:44.686549977Z"
  },
  "code": "SUCCESS"
}
```

***RESPONSE***

<strong>Response Parameters: </strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>items</code> | Object | Voucher object | (Refer to explanation below)
<code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"

<strong>Voucher object (`"item"`):</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | :---: |
<code>key</code> | String | Voucher key  | "EhQKCE1lcmNoYW50EJXVzd3wra<br>qTORIVCgdWb3VjaGVyGgpOQWtsRWZiVmRW"
<code>label</code> | String | label of voucher for merchant remarks | "Free Breakfast"
<code>voucherBathKey</code> | String | Parent key of current voucher  | "EhQKCE1lcmNoYW50EJXVzd3wraqTORIY<br>CgxWb3VjaGVyQmF0Y2gQkvnGweaB2uQg"
<code>type</code> | String | Define type of vouchers: “DISCOUNT”, “GIFT”, “CASH" | "GIFT"
<code>amount</code> | UInt | Required if type = “CASH", notation in cents, eg. RM 1.00 = 100 | 0
<code>discountRate</code> | UInt | Required if type = “DISCOUNT", notation without decimals, eg. 1% = 100 | 100
<code>minimumSpendAmount</code> | UInt | min amount to activate this voucher, required if type = “CASH”, “DISCOUNT", notation in cents, eg. RM 1.00 = 100 | 100
<code>origin</code> | String | “SYSTEM” (voucher code generated from RM server), “SELF” (voucher code uploaded from merchant csv file) | "SYSTEM"
<code>imageUrl</code> | String | Image URL of current voucher, optional | ""
<code>memberProfile</code> | String | Member profile of user's social media | ""
<code>assignedAt</code> | DateTime | Date time of voucher issuance (UTC) | "2018-09-28T17:15:17Z"
<code>qrUrl</code> | String | QR code for user to scan with Wechat or Facebook to add the voucher into their member account. | "http://api.revenuemonster.my/qr<br>/4118165203679668885/voucher/NAklEfbVdV"
<code>code</code> | String | Voucher Code, members can keep this code for future redemption. Same as the qrURL below except this code is not a URL.  | "NAklEfbVdV"
<code>isShipping</code> | Boolean | "True" if items/goods to be delivered physically to customers | false
<code>address</code> | String | Required if isShipping = true | null
<code>expiry</code> | Object of Expiry | Expiry date time of current voucher | (Refer below)
<code>usedAt</code> | DateTime | Date time of voucher being voided (UTC) | "GIFT"
<code>redeemedAt</code> | DateTime |  Date time of voucher being redeemed (UTC) | "GIFT"
<code>isDeviceRedeem</code> | Boolean |  “TRUE” means only can be redeemed through merchant app. “FALSE” means customer can do redemption from own loyalty app. | false
<code>status</code> | String | Status of current voucher: “VALID”, “ISSUE”, “REDEEMED”, “VOID”, “EXPIRED”  | "VALID"
<code>createdAt</code> | DateTime | Date time of voucher being created (UTC) | "2018-06-21T11:08:00Z"
<code>updatedAt</code> | DateTime | Date time of voucher being updated (UTC) | "2018-09-28T17:19:44.686549977Z"

<strong>Expiry object (`"expiry"`):</strong>

Parameter | Type  | Description | Example
--------- | ------- | ----------- | --- 
<code>type</code> | String | "DYNAMIC" (days from now), "FIXED" (specific fixed date) or "PERMANENT" (never expire) | "PERMANENT"
<code>day</code> | Uint | Only required by "DYNAMIC" expiry type. To indicate number of days from now until expiry. | 3
<code>expiryAt</code> | DateTime | Only required by "FIXED". To indicate specific expiry date. | "2020-10-07T17:44:26.679908+08:00"

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
   <br>
   <br>
   <br>
}
</strong>
</aside>

<!---===================--->
<!---Get Void By Code --->
<!---===================--->

##Get Voucher By Code
**Method <span style="color:Green" , bold >`Get`</span>** 

`https://sb-open.revenuemonster.my/v3/voucher/NAklEfbVdV`

To get a single voucher by code.

>Example Request

```json
curl --location --request POST "https://sb-open.revenuemonster.my/v3/voucher/NAklEfbVdV/void" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{}"
```

***REQUEST***

<strong>Request Parameters:</strong>

Specify `code` in query string (/v3/voucher/`code`)

>Example Respond

```json
{
  "item": {
    "key": "EhQKCE1lcmNoYW50EJXVzd3wraqTORIVCgdWb3VjaGVyGgpOQWtsRWZiVmRW",
    "label": "oijfge",
    "redemptionRuleKey": null,
    "voucherBatchKey": "EhQKCE1lcmNoYW50EJXVzd3wraqTORIYCgxWb3VjaGVyQmF0Y2gQkvnGweaB2uQg",
    "type": "GIFT",
    "amount": 0,
    "discountRate": 0,
    "minimumSpendAmount": 0,
    "origin": "SYSTEM",
    "imageUrl": "",
    "memberProfile": null,
    "redemptionRule": null,
    "assignedAt": "2018-09-28T17:15:17Z",
    "payload": null,
    "qrUrl": "",
    "code": "NAklEfbVdV",
    "isShipping": false,
    "address": null,
    "expiry": {
      "type": "DYNAMIC",
      "day": 100,
      "expiredAt": "2019-01-06T17:19:35Z"
    },
    "usedAt": "2018-09-28T17:19:44.686549737Z",
    "redeemedAt": "2018-09-28T17:19:35Z",
    "isDeviceRedeem": false,
    "status": "VOID",
    "createdAt": "2018-06-21T11:08:00Z",
    "updatedAt": "2018-09-28T17:19:44.686549977Z"
  },
  "code": "SUCCESS"
}
```

***RESPONSE***

<strong>Response Parameters: </strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>items</code> | Object | Voucher object | (Refer to explanation below)
<code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"

<strong>Voucher object (`"item"`):</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | :---:|
<code>key</code> | String | Voucher key  | "EhQKCE1lcmNoYW50EJXVzd3wraqT<br>ORIVCgdWb3VjaGVyGgpOQWtsRWZiVmRW"
<code>label</code> | String | label of voucher for merchant remarks | "Free Breakfast"
<code>voucherBathKey</code> | String | Parent key of current voucher  | "EhQKCE1lcmNoYW50EJXVzd3wraqTO<br>RIYCgxWb3VjaGVyQmF0Y2gQkvnGweaB2uQg"
<code>type</code> | String | Define type of vouchers: “DISCOUNT”, “GIFT”, “CASH" | "GIFT"
<code>amount</code> | UInt | Required if type = “CASH", notation in cents, eg. RM 1.00 = 100 | 0
<code>discountRate</code> | UInt | Required if type = “DISCOUNT", notation without decimals, eg. 1% = 100 | 100
<code>minimumSpendAmount</code> | UInt | min amount to activate this voucher, required if type = “CASH”, “DISCOUNT", notation in cents, eg. RM 1.00 = 100 | 100
<code>origin</code> | String | “SYSTEM” (voucher code generated from RM server), “SELF” (voucher code uploaded from merchant csv file) | "SYSTEM"
<code>imageUrl</code> | String | Image URL of current voucher, optional | ""
<code>memberProfile</code> | String | Member profile of user's social media | ""
<code>assignedAt</code> | DateTime | Date time of voucher issuance (UTC) | "2018-09-28T17:15:17Z"
<code>qrUrl</code> | String | QR code for user to scan with Wechat or Facebook to add the voucher into their member account. | "http://api.revenuemonster.my/qr<br>/4118165203679668885/voucher/NAklEfbVdV"
<code>code</code> | String | Voucher Code, members can keep this code for future redemption. Same as the qrURL below except this code is not a URL.  | "NAklEfbVdV"
<code>isShipping</code> | Boolean | "True" if items/goods to be delivered physically to customers | false
<code>address</code> | String | Required if isShipping = true | null
<code>expiry</code> | Object of Expiry | Expiry date time of current voucher | (Refer below)
<code>usedAt</code> | DateTime | Date time of voucher being voided (UTC) | "GIFT"
<code>redeemedAt</code> | DateTime |  Date time of voucher being redeemed (UTC) | "GIFT"
<code>isDeviceRedeem</code> | Boolean |  “TRUE” means only can be redeemed through merchant app. “FALSE” means customer can do redemption from own loyalty app. | false
<code>status</code> | String | Status of current voucher: “VALID”, “ISSUE”, “REDEEMED”, “VOID”, “EXPIRED”  | "VALID"
<code>createdAt</code> | DateTime | Date time of voucher being created (UTC) | "2018-06-21T11:08:00Z"
<code>updatedAt</code> | DateTime | Date time of voucher being updated (UTC) | "2018-09-28T17:19:44.686549977Z"

<strong>Expiry object (`"expiry"`):</strong>

Parameter | Type  | Description | Example
--------- | ------- | ----------- | --- 
<code>type</code> | String | "DYNAMIC" (days from now), "FIXED" (specific fixed date) or "PERMANENT" (never expire) | "PERMANENT"
<code>day</code> | Uint | Only required by "DYNAMIC" expiry type. To indicate number of days from now until expiry. | 3
<code>expiryAt</code> | DateTime | Only required by "FIXED". To indicate specific expiry date. | "2020-10-07T17:44:26.679908+08:00"


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
   <br>
   <br>
   <br>
}
</strong>
</aside>


<!---===================--->
<!---Get Voucher By Batches--->
<!---===================--->
##Get Voucher By Batches
**Method <span style="color:Green" , bold >`Get`</span>** 

`https://sb-open.revenuemonster.my/v3/voucher-batches`


To get multiple voucher batches.

***REQUEST***

<strong>Request Parameters:</strong>

No parameter required.

***RESPONSE***

<strong>Response Parameters: </strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>items</code> | []Object | Voucher object array | (Refer to explanation below)
<code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"

<strong>Voucher object (`"items"`):</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | :---: |
<code>id</code> | String | Voucher ID  | “6544507929221794245"
<code>key</code> | String | Voucher key  | "EhQKCE1lcmNoYW50EJXVzd3wraq<br>TORIVCgdWb3VjaGVyGgpOQWtsRWZiVmRW"
<code>label</code> | String | label of voucher for merchant remarks | "Free Breakfast”
<code>type</code> | String | Define type of vouchers: “DISCOUNT”, “GIFT”, “CASH" | “GIFT"
<code>amount</code> | UInt | Required if type = “CASH", notation in cents, eg. RM 1.00 = 100 | 10000
<code>discountRate</code> | UInt | Required if type = “DISCOUNT", notation without decimals, eg. 1% = 100 | 0
<code>imageUrl</code> | String | Image URL of current voucher, optional | "https://storage.googleapis.com/rm-sandbox-merchant<br>/4118165203679668885/<br>gallery/1d2721426e06da4b2b459446135da29e.jpeg”
<code>quantity</code> | UInt  | Total quantity of voucher(s) in this batch  | 1
<code>balanceQuantity</code> | UInt  | Total quantity of voucher(s) remaining in this batch |  0
<code>usedQuantity</code> | UInt  | Total quantity of voucher(s) used/assigned/redeemed in this batch  | 1
<code>expiry</code> | Object of Expiry | Expiry date time of current voucher | (Refer below)
<code>origin</code> | String | “SYSTEM” (voucher code generated from RM server), “SELF” (voucher code uploaded from merchant csv file) | “SYSTEM”
<code>isShipping</code> | Boolean | "True" if items/goods to be delivered physically to customers | false
<code>reason</code> | String | Will show if voucher batch is fail during creation. Optional. | ”"
<code>isDeviceRedeem</code> | Boolean |  “TRUE” means only can be redeemed through merchant app. “FALSE” means customer can do redemption from own loyalty app. | false
<code>createdAt</code> | DateTime | Date time of voucher being created (UTC) | "2018-06-21T11:08:00Z"
<code>updatedAt</code> | DateTime | Date time of voucher being updated (UTC) | "2018-09-28T17:19:44.686549977Z"

<strong>Expiry object (`"expiry"`):</strong>

Parameter | Type  | Description | Example
--------- | ------- | ----------- | --- 
<code>type</code> | String | "DYNAMIC" (days from now), "FIXED" (specific fixed date) or "PERMANENT" (never expire) | "PERMANENT"
<code>day</code> | Uint | Only required by "DYNAMIC" expiry type. To indicate number of days from now until expiry. | 3
<code>expiryAt</code> | DateTime | Only required by "FIXED". To indicate specific expiry date. | "2020-10-07T17:44:26.679908+08:00"


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
   <br>
   <br>
   <br>
}
</strong>
</aside>


<!---===================--->
<!---Get Voucher Batch By Key --->
<!---===================--->

##Get Voucher Batch By Key 
**Method <span style="color:Green" , bold >`Get`</span>** 

`https://sb-open.revenuemonster.my/v3/voucher-batch/EhQKCE1lcmNoYW50EJXVzd3wraqTORIYCgxWb3VjaGVyQmF0Y2gQxZP495jpsOla`

To initiate Quick Pay by scanning QR code using WeChat Pay.

>Example Request 

```json
curl --location --request GET "https://sb-open.revenuemonster.my/v3/voucher-batch/EhQKCE1lcmNoYW50EJXVzd3wraqTORIYCgxWb3VjaGVyQmF0Y2gQxZP495jpsOla" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{}"
```

***REQUEST***

<strong>Request Parameters:</strong>

Parameter | Type | Required | Description | Example
--------- | ------- | ----------- | --- | ---
<code>authCode</code> | String | Yes | Auth code of QR code/barcode being scanned. Length: 18 | "134850717797247290"
<code>order</code> | Object | Yes | Object of order | (Refer to explanation below)
<code>ipAddress</code> | String | Yes | IP address of terminal/application for payment | "8.8.8.8"
<code>terminalId</code> | String | No | ID of terminal for payment | "19382734937293"
<code>storeId</code> | String | Yes | ID of the store | "6170506694335521334"


>Example Respond

```json
{
  "item": {
    "id": "6544507929221794245",
    "key": "EhQKCE1lcmNoYW50EJXVzd3wraqTORIYCgxWb3VjaGVyQmF0Y2gQxZP495jpsOla",
    "label": "Shell Voucher",
    "type": "CASH",
    "amount": 10000,
    "discountRate": 0,
    "imageUrl": "https://storage.googleapis.com/rm-sandbox-merchant/4118165203679668885/gallery/1d2721426e06da4b2b459446135da29e.jpeg",
    "quantity": 1,
    "balanceQuantity": 0,
    "usedQuantity": 1,
    "status": "COMPLETED",
    "expiry": {
      "type": "DYNAMIC",
      "day": 1,
      "expiredAt": "2050-12-31T23:59:59Z"
    },
    "origin": "SYSTEM",
    "isShipping": false,
    "reason": "",
    "isDeviceRedeem": true,
    "createdAt": "2018-09-21T07:12:31Z",
    "updatedAt": "2018-09-26T07:15:54Z"
  },
  "code": "SUCCESS"
}
```
***RESPONSE***

<strong>Response Parameters: </strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>items</code> | Object | Transaction object | (Refer to explanation below)
<code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"

<strong>Voucher object (`"item"`):</strong>

Parameter | Type | Description | Example
|---------|------|-------------| :--------:
<code>id</code> | String | Voucher ID  | “6544507929221794245"
<code>key</code> | String | Voucher key  | "EhQKCE1lcmNoYW50EJXVzd3wraqTORIV<br>CgdWb3VjaGVyGgpOQWtsRWZiVmRW"
<code>label</code> | String | label of voucher for merchant remarks | "Free Breakfast”
<code>type</code> | String | Define type of vouchers: “DISCOUNT”, “GIFT”, “CASH" | “GIFT"
<code>amount</code> | UInt | Required if type = “CASH", notation in cents, eg. RM 1.00 = 100 | 10000
<code>discountRate</code> | UInt | Required if type = “DISCOUNT", notation without decimals, eg. 1% = 100 | 0
<code>imageUrl</code> | String | Image URL of current voucher, optional | "https://storage.googleapis.com/rm-sandbox-merchant<br>/4118165203679668885/gallery/1d2721426e06da4b2b459446135da29e.jpeg”
<code>quantity</code> | UInt  | Total quantity of voucher(s) in this batch  | 1
<code>balanceQuantity</code> | UInt  | Total quantity of voucher(s) remaining in this batch |  0
<code>usedQuantity</code> | UInt  | Total quantity of voucher(s) used/assigned/redeemed in this batch  | 1
<code>expiry</code> | Object of Expiry | Expiry date time of current voucher | (Refer below)
<code>origin</code> | String | “SYSTEM” (voucher code generated from RM server), “SELF” (voucher code uploaded from merchant csv file) | “SYSTEM”
<code>isShipping</code> | Boolean | "True" if items/goods to be delivered physically to customers | false
<code>reason</code> | String | Will show if voucher batch is fail during creation. Optional. | ”"
<code>isDeviceRedeem</code> | Boolean |  “TRUE” means only can be redeemed through merchant app. “FALSE” means customer can do redemption from own loyalty app. | false
<code>createdAt</code> | DateTime | Date time of voucher being created (UTC) | "2018-06-21T11:08:00Z"
<code>updatedAt</code> | DateTime | Date time of voucher being updated (UTC) | "2018-09-28T17:19:44.686549977Z"

<strong>Expiry object (`"expiry"`):</strong>

Parameter | Type  | Description | Example
--------- | ------- | ----------- | --- 
<code>type</code> | String | "DYNAMIC" (days from now), "FIXED" (specific fixed date) or "PERMANENT" (never expire) | "PERMANENT"
<code>day</code> | Uint | Only required by "DYNAMIC" expiry type. To indicate number of days from now until expiry. | 3
<code>expiryAt</code> | DateTime | Only required by "FIXED". To indicate specific expiry date. | "2020-10-07T17:44:26.679908+08:00"


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
   <br>
   <br>
   <br>
}
</strong>
</aside>

<!---===================--->
<!---Get Voucher By Batch Key --->
<!---===================--->

##Get Vouchers By Batch Key
**Method <span style="color:Green" , bold >`Get`</span>** 

`https://sb-open.revenuemonster.my/v3/voucher-batch/EhQKCE1lcmNoYW50EJXVzd3wraqTORIYCgxWb3VjaGVyQmF0Y2gQi5rUhcrdx78V/vouchers`

To initiate Quick Pay by scanning QR code using WeChat Pay.

>Example Request 

```json
curl --location --request GET "https://sb-open.revenuemonster.my/v3/voucher-batch/EhQKCE1lcmNoYW50EJXVzd3wraqTORIYCgxWb3VjaGVyQmF0Y2gQi5rUhcrdx78V/vouchers" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585"
```


***REQUEST***

<strong>Request Parameters:</strong>

Parameter | Type | Required | Description | Example
--------- | ------- | ----------- | --- | ---
<code>authCode</code> | String | Yes | Auth code of QR code/barcode being scanned. Length: 18 | "134850717797247290"
<code>order</code> | Object | Yes | Object of order | (Refer to explanation below)
<code>ipAddress</code> | String | Yes | IP address of terminal/application for payment | "8.8.8.8"
<code>terminalId</code> | String | No | ID of terminal for payment | "19382734937293"
<code>storeId</code> | String | Yes | ID of the store | "6170506694335521334"

>Example Respond

```json
{
  "items": [
    {
      "key": "EhQKCE1lcmNoYW50EJXVzd3wraqTORIWCgdWb3VjaGVyGgtVVUVyYTIyVlN5Mg",
      "label": "test",
      "voucherBatchKey": "EhQKCE1lcmNoYW50EJXVzd3wraqTORIYCgxWb3VjaGVyQmF0Y2gQi5rUhcrdx78V",
      "type": "CASH",
      "amount": 100,
      "discountRate": 0,
      "minimumSpendAmount": 0,
      "origin": "SYSTEM",
      "imageUrl": "",
      "memberProfile": {
        "id": "1039768290679711875",
        "name": "yussuf",
        "email": "yussuf888@gmail.com",
        "nric": "",
        "address": {
          "addressLine1": "",
          "addressLine2": "",
          "postcode": "",
          "city": "",
          "state": "",
          "country": ""
        },
        "gender": "",
        "state": "",
        "birthDate": "0001-01-01T00:00:00Z",
        "loyaltyPoint": 0,
        "credit": 112,
        "countryCode": "60",
        "phoneNumber": "176473298",
        "profileImageUrl": "https://storage.googleapis.com/rm-sandbox-asset/img/avatar.png",
        "hasPinCode": false,
        "memberTier": null,
        "status": "ACTIVE",
        "createdAt": "2018-10-19T03:39:47Z"
      },
      "assignedAt": "0001-01-01T00:00:00Z",
      "qrUrl": "",
      "code": "UUEra22VSy2",
      "isShipping": false,
      "address": null,
      "expiry": {
        "type": "DYNAMIC",
        "day": 1,
        "expiredAt": "2050-12-31T23:59:59Z"
      },
      "usedAt": "0001-01-01T00:00:00Z",
      "redeemedAt": "2019-03-22T04:58:38Z",
      "isDeviceRedeem": true,
      "status": "REDEEMED",
      "voucherComboKey": null,
      "createdAt": "2019-02-01T03:13:19Z",
      "updatedAt": "2019-03-13T03:16:26Z"
    }
  ],
  "code": "SUCCESS",
  "meta": {
    "count": 1
  }
}
```

***RESPONSE***

<strong>Response Parameters: </strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>items</code> | Object | Transaction object | (Refer to explanation below)
<code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"

<strong>Voucher object (`"item"`):</strong>

Parameter | Type | Description | Example
----- | ----- | -----| -----|
<code>id</code> | String | Voucher ID  | “6544507929221794245"
<code>key</code> | String | Voucher key  | "EhQKCE1lcmNoYW50EJXVzd3wraqTORIVCgdWb3VjaGVyGgpOQWtsRWZiVmRW"
<code>label</code> | String | label of voucher for merchant remarks | "Free Breakfast”
<code>type</code> | String | Define type of vouchers: “DISCOUNT”, “GIFT”, “CASH" | “GIFT"
<code>amount</code> | UInt | Required if type = “CASH", notation in cents, eg. RM 1.00 = 100 | 10000
<code>discountRate</code> | UInt | Required if type = “DISCOUNT", notation without decimals, eg. 1% = 100 | 0
<code>imageUrl</code> | String | Image URL of current voucher, optional | "https://storage.googleapis.com/rm-sandbox-merchant/4118165203679668885/gallery/1d2721426e06da4b2b459446135da29e.jpeg”
<code>quantity</code> | UInt  | Total quantity of voucher(s) in this batch  | 1
<code>balanceQuantity</code> | UInt  | Total quantity of voucher(s) remaining in this batch |  0
<code>usedQuantity</code> | UInt  | Total quantity of voucher(s) used/assigned/redeemed in this batch  | 1
<code>expiry</code> | Object of Expiry | Expiry date time of current voucher | (Refer below)
<code>origin</code> | String | “SYSTEM” (voucher code generated from RM server), “SELF” (voucher code uploaded from merchant csv file) | “SYSTEM”
<code>isShipping</code> | Boolean | "True" if items/goods to be delivered physically to customers | false
<code>reason</code> | String | Will show if voucher batch is fail during creation. Optional. | ”"
<code>isDeviceRedeem</code> | Boolean |  “TRUE” means only can be redeemed through merchant app. “FALSE” means customer can do redemption from own loyalty app. | false
<code>createdAt</code> | DateTime | Date time of voucher being created (UTC) | "2018-06-21T11:08:00Z"
<code>updatedAt</code> | DateTime | Date time of voucher being updated (UTC) | "2018-09-28T17:19:44.686549977Z"


<strong>Expiry object (`"expiry"`):</strong>

Parameter | Type  | Description | Example
--------- | ------- | ----------- | --- 
<code>type</code> | String | "DYNAMIC" (days from now), "FIXED" (specific fixed date) or "PERMANENT" (never expire) | "PERMANENT"
<code>day</code> | Uint | Only required by "DYNAMIC" expiry type. To indicate number of days from now until expiry. | 3
<code>expiryAt</code> | DateTime | Only required by "FIXED". To indicate specific expiry date. | "2020-10-07T17:44:26.679908+08:00"

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
   <br>
   <br>
   <br>
}
</strong>
</aside>
