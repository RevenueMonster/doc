#Generate Access Token#

This endpoint is to obtain access token for subsequent calls.

**What is refresh token?**
Refresh token is used to get new access token when:

* Access token is expired (2 hours)
* Access token is compromised/hacked/stolen/destroyed

In case you lost refresh token or do not want to deal with refresh token, you may opt to get new access token/refresh token using client credentials again. But this is not a suggested practice. *(You don't want your clientid/clientscrect always exposed in network traffic. That is why you shall use refresh token.)*

Recommended practice is to run a scheduled task to get the refresh token refreshed before 2 years expiry. And store it using singleton design pattern for all subsequent requests to get access token. *(For example, static variable in most OOP languages like C# or JAVA)*. Another fail-safe mechanism is that if a invalid access token error has occur, use clientid/clientsecrect again to get new access token and refresh token and store the access token/refresh token for future use.

##Client Credentials 
 
 **Method : <span style="color:Orange" , bold >POST</span>**

 `https://sb-oauth.revenuemonster.my/v1/token` (SandBox)

  `https://oauth.revenuemonster.my/v1/token` (Production)

  > Example Request

```json
curl --location --request POST "https://sb-oauth.revenuemonster.my/v1/token" \
  --header "Content-Type: application/json" \
  --header "Authorization: Basic NjY5MTY1ODE1MDQ5NjMyNzA1MTptNzFwc3dibVFWQzBpTXNHc000TEZMSUl4czZsWEV6eA==" \
  --data "{
  \"grantType\": \"client_credentials\"
}"
```
**Process flow for Grant Type: `client_credentials`**

This is for the scenario that merchant's trusted developer is provided with clientid and clientsecret.

1. To start with, get OAuth 2.0 client credentials (`client_id` & `client_secret`) from your [RM Merchant Portal](https://merchant.revenuemonster.my/). Then request an access token from RM Authorisation Server, you will get a response consists of access token & refresh token. Use the access token to call Revenue Monster API that you want to access. Refresh token can be stored to get new access tokens.

2. Get an access token from RM Authorization Server Access token is required for subsequent request to our resource server(s) to get protected resources.

> Example Response 

``` json
{
  "accessToken": "eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiYXBpX2NsaWVudEBFaGNLQzA5QmRYUm9RMnhwWlc1MEVJbmVpOW5mbE9DN0ZRIl0sImV4cCI6MTU1NjQxNjA4MSwiaWF0IjoxNTUzODI0MDgxLCJpc3MiOiJodHRwczovL3NiLW9hdXRoLnJldmVudWVtb25zdGVyLm15IiwianRpIjoiRWh3S0VFOUJkWFJvUVdOalpYTnpWRzlyWlc0UW92Mk1pOUxZa3NnViIsIm5iZiI6MTU1MzgyNDA4MSwic3ViIjoiRWhRS0NFMWxjbU5vWVc1MEVKWFZ6ZDN3cmFxVE9SSVFDZ1JWYzJWeUVJeUpxSXp2eU1QVmNRIn0.NpnDCdRfjlzJpLMU_cHY4jmyXMW63wpyh99vsu3CIt1jyaQlD34icxfh5MTMytJ7Irtp--K9uy8BuRlt5PM7ufqBVCFOEfC8uXs89DJFx1z2qB2r4QwGreQ7GmG2qQhTPkRtz4al-kCgifUkPQkf1GYS7Ly8VNXGTNMtWT4Ko4juEs8sT-D7ya2zgs81RTxZw8pFmwp78cCZviTZ5zGuVYjZ73EQu_N0GAMaj0D18HdiIRzaSRZh-rIN3z6Lfy_wpvtGNYRpMasSBYiIKOLcExtU8tPiRET39awBFaT7qPKslse7NXSdNNqqwDYIC0-WZKn7rzmIXbtVQRllQn0ing",
  "tokenType": "Bearer",
  "expiresIn": 393612,
  "refreshToken": "PScHXFQHCaAOPrPLNtzktDyRWzrjNhgMLcqZsVRBuGfcvrjDjaMQZSFIHXOGwmnGOSWyrfPncvivwCloQCEToDBGmZhRMufFTDzKpZOzEWsZMDvxYrvDARhrHIaDDkWA",
  "refreshTokenExpiresIn": 243113245
}

```
-**Step 1:**

Prepare Request Header:

| Parameter | Type | Required | Description| Example  
|:----------|:----:|:---------:| :------------------| :--------: |
| `ClientID`| String| Yes | Client ID or AppID as obtained from [RM Merchant Portal](https://merchant.revenuemonster.my/). | 3208919753194101125
| `ClientSecret`| String| Yes | Client secret or AppSecret as obtained from [RM Merchant Portal](https://merchant.revenuemonster.my/).| mglve4W3UhPSGOV7gnwoYKyvbRCe83zZ


-**Step 2:**

Encode the parameters from Step 1 in Base 64 format.

 Structure: <br />
`clientId`:`clientSecret` 

 Eg: <br />
Before Base64 encoding: <br />
`3675930941412424316:wmn7FUauXHdkoYa9182kCMkjGnNJVgin`

After Base64 encoding: <br />
`MzY3NTkzMDk0MTQxMjQyNDMxNjp3bW43RlVhdVhIZGtvWWE5MTgya0NNa2pHbk5KVmdpbg==`



-**Step 3:**

 Put the Base64 encoded `clientId` and `clientSecret` in Headers:


<code>Content-Type: application/json <br />
Authorization: Basic MzY3NTkzMDk0MTQxMjQyNDMxNjp3bW43RlVhdVhIZGtvWWE5MTgya0NNa2pHbk5KVmdpbg==</code>

More info refer: <https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication>

* Body : 

**Request Parameters:**

| Parameter | Type | Required | Description | Example 
| :--------:| :---:|:----------:| ------------| :--------: |
|`grantType` | String | Yes | Only support client credentials or authorisation code | client_credentials

**Response Parameters :**

| Parameter | Type | Description | Example
| :---------|:----:|-------------|------:
|`accessToken` | String | Required for subsequent request(s) | Access Token
|`tokenType` | String | We only support “Bearer” type | Bearer
|`expiresIn` | String | Token expiry, in seconds format. “7200” means 7,200 seconds or 2 hour | 7200
|`refreshToken` | String | Required for getting new access token after expiry | Refresh token string

**HEADERS**

**Content-Type**  &nbsp; &nbsp; application/json <br />

**AuthorizationBasic**    &nbsp; <br />  OTExMjU1NzcyODk3Njg0NjYyMjpUQVBPaWZ2UHl1T3FhYkVZV0hwQ3JSaU1EZE1UTWdGeg==

**BODY** <br />

`{
  "grantType": "client_credentials"
}`

<!--===================--->
<!--Authorization Code-->
<!--===================--->

##Authorization Code

**Method : <span style="color:Orange" , bold >POST</span>**

`https://sb-oauth.revenuemonster.my/v1/token`

**Process flow for Grant Type:** `auth_code`
This is for the scenario which a partner wants to request permission to develop an application of a merchant.

For authorization code, only `client_id` is needed. You are required to pass in following request parameters as Query String.

1. Get Authorization code from RM Merchant Portal

**Request Parameters :**

Parameter | Type | Required | Description | Example |
--------- | ---- | -------- | ----------- | ------- |
`responseType` | String | Yes | Only support authorization code | code 
`clientId` | String | Yes | Client ID or AppID as obtained from [RM Merchant Portal](https://merchant.revenuemonster.my/). | 3675930941412424316
`redirectUri` | String | Yes | Specify your desired redirect Uri after request successful. This Uri must be EXACTLY the same as the one entered in [RM Merchant Portal](https://merchant.revenuemonster.my/) |  <https://www.google.com>
`scope` | String | Yes | Scope of authorization granted to user, to perform action(s) when calling other API endpoints. (Currently only support `manage_payment`, `get_merchant_profile`, `get_user_profile`, `manage_store`). Separated by comma(s) without space. | manage_payment 
`state` | String | No | Optional field for user reference, will be passed back in response | Anything 

**Response Parameters**

Parameter | Type | Description | Example | 
----------| ---- | ----------- | ------- |
`code` | String | Required for subsequent request(s) | Random string
`state` | String | Optional field for user reference | Anything 

Example Request URL :
 <br />
 <a href="https://sb-oauth.revenuemonster.my/authorize?responseType=code&clientId=3675930941412424316& redirectUri=https://www.google.com&scope=manage_payment&state=123456">
 https://sb-oauth.revenuemonster.my/authorize?responseType=code&clientId=3675930941412424316&redirectUri=
 https://www.google.com&scope=manage_payment&
 state=123456</a>


![image](images/authRespond.png)

Example Response URL : 
<br />
<a href="https://www.google.com/?code=iEWqJsA5KVEsWF11xTphDIx8vbUqomsiW2vT4KClOFaVqiGh517dDCfgPlHlqZUeP5atf0SnwiMO8P2X06md8Muv4nEWRW9nro6a5ef0M1jD7k1EFOh9fPV7Jvoe7wIRoVY6JYCSzHuWItQ3Un9J137smxcdSkZ8GKs14vDmREtwFsn8a0SSKBvgfjXEJGrWnCZaCOpEhXPDNzIfo71n0p8p38d9mUyNqxYpQ8UzlPpfAKEr0fiGIFTf6RakxUp&state=123456">https://www.google.com/?code=iEWqJsA5KVEsWF11xTphDIx8vbUqomsiW2vT4KClOFaVqiGh517
dDCfgPlHlqZUeP5atf0SnwiMO8P2X06md8Muv4nEWRW9nro6a5ef0M1jD7k1EFOh9f
PV7Jvoe7wIRoVY6JYCSzHuWItQ3Un9J137smxcdSkZ8GKs14vDmREtwFsn8a0SSKBvg
fjXEJGrWnCZaCOpEhXPDNzIfo71n0p8p38d9mUyNqxYpQ8UzlPpfAKEr0fiGIF
Tf6RakxUp&state=123456</a>


<aside class="notice">
<br />
-  From the redirected response URI, we can get authorization code from the query string, as follow:- <br />
<code>iEWqJsA5KVEsWF11xTphDIx8vbUqomsiW2vT4KClOFaVqiGh517dDCfgPlHlqZUeP5atf0SnwiMO8P2X06md8Muv4nEWRW9nro6a5ef0M1jD7k1EFOh9fPV7Jvoe7wIRoVY6JYCSzHuWItQ3Un9J137smxcdSkZ8GKs14vDmREtwFsn8a0SSKBvgfjXEJGrWnCZaCOpEhXPDNzIfo71n0p8p38d9mUyNqxYpQ8UzlPpfAKEr0fiGIFTf6RakxUp</code><br /><br />

- Thereafter, user may use this code to generate access token and hence proceed to call other endpoints.<br /><br />

- This code is valid for <b>ONE-TIME</b> only. Once used <b>(either successful or failed)</b>, you are required to request a new authorization code using the steps before.
 </aside>
 
  **Get an access token from RM Authorization Server**
 <br />

* Step 1: <br />

Parameter | Type | Required | Description | Example
--------- | ------- | ----------- | ----------- | ---
<code>clientId</code> | String | Yes | Client ID or AppID as obtained from [RM Merchant Portal](https://merchant.revenuemonster.my/ "RM Merchant Portal"). | 3208919753194101125
<code>clientSecret</code> | String | Yes | Client secret or AppSecret as obtained from [RM Merchant Portal](https://merchant.revenuemonster.my/ "RM Merchant Portal"). | mglve4W3UhPSGOV7gnwoYKyvbRCe83zZ


> Example Request

```json 
curl --location --request POST "https://sb-oauth.revenuemonster.my/v1/token" \
  --header "Content-Type: application/json" \
  --header "Authorization: Basic NjY5MTY1ODE1MDQ5NjMyNzA1MTptNzFwc3dibVFWQzBpTXNHc000TEZMSUl4czZsWEV6eA==" \
  --data "{
  \"grantType\": \"authorization_code\",
  \"code\": \"kDHVY8IrbUU5nAAaZyz5WxFqFEh2LOx4Qqom7chiu1bmCrAE6fWTSKm5O39NwKyLZdHdZtlrQc9idG2o42P10WOMibH06r0XEWLCaPfkQgE9X7VcihAVXTxOlJxpLW9kTydaaSEuz5tIlyVdluEwXx8ck2plRzbezf3vFex32Lic84cjxh8yrMEM4sTo9AdAOUBvBavZpkB2ZkTIy0LdPY0En0ofsm4JmbWxifCsNcuMUYNKGBmDvNatvQzQtGI\",
  \"redirectUri\": \"https://revenuemonster.my\"
}"
```

* Step 2:<br>
Encode the parameters from Step 1 in **Base 64** format.

Structure: <br> 
`clientId`:`clientSecret` <br>

Before encoding using Base64 :<br>
`3675930941412424316:wmn7FUauXHdkoYa9182kCMkjGnNJVgin`

Eg encoding using Base64 :<br>
`MzY3NTkzMDk0MTQxMjQyNDMxNjp3bW43RlVhdVhIZGtvWWE5MTgya0NNa2pHbk5KVmdpbg==`

* Step 3:<br>
 - Put the Base64 encoded `clientId` and `clientSecret` in Headers:

>Example Response

```json
{
  "accessToken": "eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiY2xpZW50QEVoY0tDMDlCZFhSb1EyeHBaVzUwRUl1cnVkV2s5T0x1WEEiXSwiZXhwIjoxNTIzNDYwNDc3LCJpYXQiOjE1MjM0NTMyNzcsImlzcyI6Imh0dHA6Ly8xOTIuMTY4LjAuMTk1OjgwODIiLCJqdGkiOiJFaHdLRUU5QmRYUm9RV05qWlhOelZHOXJaVzRROF9iMDJJYlNrcUFMIiwibmJmIjoxNTIzNDUzMjc3LCJzdWIiOiJFaFFLQ0UxbGNtTm9ZVzUwRUkzZF9vTDd3dXUzV0JJUUNnUlZjMlZ5RUl5dmctV2Q3Y3F0S1EifQ.Cqa4gWIApb8yL3zvY8-PDgrVUV9cli3MrLxFcE4vkXi1PIfczK6A3B9GhTIQ6fJJizlbkmHgTKk7VIVFfWPPSgGOR3_FcKPBSd3BwlIKHVL2U4bHOVFdNy81gusZJ_tEXJIL86wEhcZs_5XtAIBcqGHgATjvQIwGVqXt3gqhsu8kGBfy7MGo3DdDdcioQE8lisJJ9JNVzzXzxG2iWJBWG3un9suEuADIGOkGkirdgjbd5Oxbzi4Jrxfq5JSwqn7DwH_jkOqg8kqvNtJ5yUU0W1Z9NYFn4eq8i67xuvo6tmqICsihelARPbZ_qqA85Ovlm8EHpaEYOj_P4iugWOIFeg",
  "tokenType": "Bearer",
  "expiresIn": 7200,
  "refreshToken": "kgy2b68e1JYpQjZhriwQM0j7pJ35PIfeCQEnK3PDcKtA0x0IgvmBucxmSpJVsDYYJ2GyMCHLcBbfHP6rGm32T1rQuGBvHl8mh539HJmEk4geRE1eMmKh79SwhsN0C3F83ahuNbcEIG8WxFmaRLozK0vf5XHmHy1610hcUNFqUhhT7Dyl33DcqO53DohZ7RXAINmoVMpwiNlFURE0KzVzjmhW5jt6IiTkbcpCUAKPiRtaSI7GzKWoBHnPl8W6jWA4"
}
```

<code>
Content-Type: application/json <br />
Authorization: Basic MzY3NTkzMDk0MTQxMjQyNDMxNjp3bW43RlVhdVhIZGtvWWE5MTgya0NNa2pHbk5KVmdpbg==
</code>

(More info refer: <https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication>)

- Body:

<strong>Request Parameters:</strong>

Parameter | Type | Required | Description | Example
--------- | ------- | ----------- | ----------- | ---
<code>grantType</code> | String | Yes | Only support client credentials or authorisation code | authorization_code
<code>code</code> | String | Yes | Code obtained from query string as described in previous steps. | Random String
<code>redirectUri</code> | String | Yes | Must be *EXACTLY* the same as described in previous steps. | https://www.google.com


<strong>Response Parameters:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>accessToken</code> | String | Required for subsequent request(s) | Access Token
<code>tokenType</code> | String | We only support “Bearer” type  | Bearer
<code>expiresIn</code> | String | Token expiry, in seconds format. “7200” means 7,200 seconds or 2 hour | 7200
<code>refreshToken</code> | String | Required for getting new access token after expiry | Refresh token string


<!--===================--->
<!--Refresh Token-->
<!--===================--->

##Refresh Token 

**Method : <span style="color:Orange" , bold >POST</span>**

`https://sb-oauth.revenuemonster.my/v1/token`

Access token will be expired as mentioned in response parameter (currently default expiry is set to 2 hours). Developers can regenerate new access token by using refresh token rather than using clientid/clientserect. 

- Step 1:<br />
<strong>Prepare Request Header:</strong>

Parameter | Type | Required | Description | Example
--------- | ------- | ----------- | ----------- | ---
<code>clientId</code> | String | Yes | Client ID or AppID as obtained from [RM Merchant Portal](https://merchant.revenuemonster.my/ "RM Merchant Portal"). | 3208919753194101125
<code>clientSecret</code> | String | Yes | Client secret or AppSecret as obtained from [RM Merchant Portal](https://merchant.revenuemonster.my/ "RM Merchant Portal"). | mglve4W3UhPSGOV7gnwoYKyvbRCe83zZ

- Step 2:<br>
Encode the parameters from Step 1 in Base 64 format.

Structure: <br> 
`clientId`:`clientSecret` <br>

Before encoding using Base64 :<br>
`3675930941412424316:wmn7FUauXHdkoYa9182kCMkjGnNJVgin`

Eg encoding using Base64 :<br>
`MzY3NTkzMDk0MTQxMjQyNDMxNjp3bW43RlVhdVhIZGtvWWE5MTgya0NNa2pHbk5KVmdpbg==`


- Step 3:<br>
    - Put the Base64 encoded `clientId` and `clientSecret` in Headers:

 > Example Request

```json
curl --location --request POST "https://sb-oauth.revenuemonster.my/v1/token" \
  --header "Content-Type: application/json" \
  --header "Authorization: Basic MTM5NjMxNzEzNjIyMzY4MzExMjpEWGxaTWpQem96dXh2Z2JRRmtYWmFDcnFoRmliS3B4ZQ==" \
  --data "{
  \"grantType\": \"refresh_token\",
  \"refreshToken\": \"OgoHjoZyLZPnHemifOrHIwStdeyzKuFoDaJBtBRULxEIJgANlhsLgFuBFiVTtqiQgmYDOTBkakwXZWfcLqXQTUTiqCpQTAEVHuqshWdiuvtGMIYztLiVfEmLEoXNlALi\"
}"
```

<code>
Content-Type: application/json <br />
Authorization: Basic MzY3NTkzMDk0MTQxMjQyNDMxNjp3bW43RlVhdVhIZGtvWWE5MTgya0NNa2pHbk5KVmdpbg==
</code>

(More info refer: <https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication>)

- Body:

<strong>Request Parameters:</strong>

Parameter | Type | Required | Description | Example
--------- | ------- | ----------- | ----------- | ---
<code>grantType</code> | String | Yes | Only support refresh_token | refresh_token
<code>refreshToken</code> | String | Yes | Refresh token is obtained from response parameter when access token is generated. | Random String

> Example Request

```json 
{
    "accessToken": "eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiYXBpX2NsaWVudEBFaGNLQzA5QmRYUm9RMnhwWlc1MEVJbmVpOW5mbE9DN0ZRIl0sImV4cCI6MjM0NDQyOTc0OSwiaWF0IjoxNTU2MDI5NzQ5LCJpc3MiOiJodHRwczovL3NiLW9hdXRoLnJldmVudWVtb25zdGVyLm15IiwianRpIjoiRWh3S0VFOUJkWFJvUVdOalpYTnpWRzlyWlc0UXJ1dkxrSUthaU13ViIsIm5iZiI6MTU1NjAyOTc0OSwic3ViIjoiRWhRS0NFMWxjbU5vWVc1MEVKWFZ6ZDN3cmFxVE9SSVFDZ1JWYzJWeUVJeUpxSXp2eU1QVmNRIn0.PL3u_qTOw1c51HWNJsgTVDQBIZssLMRT2Nuo95_qyHHRTOhYz_LPtFdnICabU8P77lBOtZR5rMTuw3jzFFUopu3mCfT6ULzLtbBMVtlwXRdAZAw-kecYIhG5AmkT7H7Iwskvpitkqp1G31xb6PPOEhNTiO3iUY_Q-o3lsjn8uAWdDn7oXdWSmTMCI-1Mo0eYpWIQxsMI6HdQKXzhn1NELE1zvedyUhb6syw3oIocL7yll2eMg_LcYMdTOh26Ae614an8m7zSxgSBydwMHC0gjf7mzYEgqUzJ0M7zg_-vHy67u5UrysXQXDx-1MVHXaetzh3RriCR0R0_qESnIge3SQ",
    "tokenType": "Bearer",
    "expiresIn": 788399999,
    "refreshToken": "XtBwKribhoPsoEbhHnLNJSjkSuskqsRIpTnvVxmOTyQhenqlgGQisbtbpcjcapmhPEaHrJZVbPGvkvaTwWozamuCBUfvWdWQzHJSnjpuurEACugOZssEpUffUSDoSxLz",
    "refreshTokenExpiresIn": 1576799999
}
```

<strong>Response Parameters:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>accessToken</code> | String | Required for subsequent request(s) | Access Token
<code>tokenType</code> | String | We only support “Bearer” type  | Bearer
<code>expiresIn</code> | String | Token expiry, in seconds format. “7200” means 7,200 seconds or 2 hour | 7200
<code>refreshToken</code> | String | Required for getting new access token after expiry | Refresh token string


<!--===================--->
<!--Revoke Token-->
<!--===================--->

<!--##Revoke Token 

**Method : <span style="color:Orange" , bold >POST</span>**

`https://sb-oauth.revenuemonster.my/v1/revoke`

Process flow for Grant Type: `client_credentials`


Get OAuth 2.0 credentials from RM Merchant Portal Go to RM Merchant Portal to get your client credentials, ie. client ID and client secret that will be stored in both RM server and your application. How to get your client credentials on Merchant Portal

Get an access token from RM Authorization Server Access token is required for subsequent request to our resource server(s) to get protected resources.

https://sb-oauth.revenuemonster.my: (https://sb-oauth.revenuemonster.my)[https://sb-oauth.revenuemonster.my]

Step 1:<br>
<strong>Prepare Request Header:</strong>

Parameter | Type | Required | Description | Example
--------- | ------- | ----------- | ----------- | ---
<code>clientId</code> | String | Yes | Client ID or AppID as obtained from [RM Merchant Portal](https://merchant.revenuemonster.my/ "RM Merchant Portal"). | 3208919753194101125
<code>clientSecret</code> | String | Yes | Client secret or AppSecret as obtained from [RM Merchant Portal](https://merchant.revenuemonster.my/ "RM Merchant Portal"). | mglve4W3UhPSGOV7gnwoYKyvbRCe83zZ

Step 2:<br>
Encode the parameters from Step 1 in Base 64 format.

Structure: <br> 
`clientId`:`clientSecret` <br>
Eg:<br>
Before Base64 encoding:<br>
`3675930941412424316:wmn7FUauXHdkoYa9182kCMkjGnNJVgin`

After Base64 encoding:<br>
`MzY3NTkzMDk0MTQxMjQyNDMxNjp3bW43RlVhdVhIZGtvWWE5MTgya0NNa2pHbk5KVmdpbg==`

Step 3:<br>
- Put the Base64 encoded `clientId` and `clientSecret` in Headers:

(More info refer: https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication)

- Body:

<strong>Request Parameters:</strong>

Parameter | Type | Required | Description | Example
--------- | ------- | ----------- | ----------- | ---
<code>grantType</code> | String | Yes | Only support client credentials or authorisation code | client_credentials

<strong>Response Parameters:</strong>---->

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>accessToken</code> | String | Required for subsequent request(s) | JWE Token (Refer)
<code>tokenType</code> | String | We only support “Bearer” type  | Bearer
<code>expiresIn</code> | String | Token expiry, in seconds format. “7200” means 7,200 seconds or 2 hour | 7200
<code>refreshToken</code> | String | Required for getting new access token after expiry | Refresh token string
<code>scope</code> | String | Scope of authorization granted to user, to perform action(s) when calling other API endpoints. (Currently only support `manage_payment`, `get_merchant_profile`, `get_user_profile`). Separated by comma(s) without space.  | manage_payment,get_user_profile