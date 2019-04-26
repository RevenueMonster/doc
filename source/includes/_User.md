#User 
To query for ALL users under this merchant.

- Scope: `get_user_profile`
- Authentication: Access token obtained from [Generate Access Token](https://doc.revenuemonster.my/#66368026-71ee-4640-8ad7-208f843c6d6c) into `Authorization` header value as `Bearer [access_token]`.

##Get User 
**Method <span style="color:green" , bold >`GET`</span>**

<code>https://sb-open.revenuemonster.my/v3/user</code>

>Example Request 

```json
curl --location --request GET "https://sb-open.revenuemonster.my/v3/user" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 HeVHowOfhueqMqUU6+ZawOgG5esSGi/DYoobUC/GUnUJqeVOtIJUpb+XzSIfaoJoraceaZE8lbjNKkM8tNCDRA==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1527407052" \
  --data "{

}"
```

***REQUEST***

<strong>Request Parameters:</strong>

*Note: No request parameter is required for this endpoint*

Eg. Plain Text Parameters:

`method=get&nonceStr=VYNknZohxwicZMaWbNdBKUrnrxDtaRhN&requestUrl=https://sb-open.revenuemonster.my/v3/user&signType=sha256&timestamp=1527407052`


***RESPONSE***

<strong>Response Parameters:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>items</code> | Object[] | Array of user object | (Refer to explanation below)
<code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"


>Example Respond

```json
{
  "item": {
    "id": "2728070797661038926",
    "firstName": "M",
    "lastName": "YUSSUF",
    "countryCode": "60",
    "phoneNumber": "176473298",
    "email": "yussuf@revenuemonster.my",
    "avatarUrl": "https://storage.googleapis.com/rm-dev-asset/img/avatar.png",
    "status": "ACTIVE",
    "storeId": [
      "6883264812332703106"
    ],
    "isActive": true,
    "createdAt": "2018-05-14T09:26:23Z",
    "updatedAt": "2018-05-15T03:29:56Z"
  },
  "code": "SUCCESS"
}
```

<strong>Array of store object (`"items"`):</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>id</code> | String | User ID | “8190656045166232716”
<code>firstName</code> | String | First name of user  | “MOHAMED”
<code>lastName</code> | String | Last name of user | “YUSSUF”
<code>countryCode</code> | String | Country code of user contact number | "60"
<code>phoneNumber</code> | String | Phone number of user | "377334080"
<code>email</code> | String | Email address of user | "yussuf@revenuemonster.my"
<code>avatarUrl</code> | String | Public URL to show user’s avatar | "https://storage.googleapis.com/rm-prod-asset/img/avatar.png"
<code>status</code> | String | Current status of user | “ACTIVE”
<code>storeId</code> | String | Store ID | "6170506694335521334"
<code>isActive</code> | Boolean | User active or deactivated status | true
<code>createdAt</code> | DateTime | Creation date time of user | "2018-02-12T08:53:13Z"
<code>updatedAt</code> | DateTime | Last update date time of user | "2018-02-12T08:53:13Z"
