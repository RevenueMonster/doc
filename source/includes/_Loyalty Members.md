#Loyalty Members 
##Get Loyalty Members
**Method <span style="color:Green" , bold >`Get`</span>** 

>Example Request 

```json
curl --location --request GET "https://sb-open.revenuemonster.my/v3/loyalty/members" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{

}"
```

`https://sb-open.revenuemonster.my/v3/loyalty/members`



>Example Respond 

```json
{
  "items": [
    {
      "id": "2940921291529816182",
      "name": "Gan",
      "email": "junkai@revenuemonster.my",
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
      "countryCode": "60",
      "phoneNumber": "167367171",
      "profileImageUrl": "https://storage.googleapis.com/rm-sandbox-asset/img/avatar.png",
      "memberTier": null,
      "status": "ACTIVE",
      "createdAt": "2018-09-19T10:00:21Z"
    },
    {
      "id": "3328113896344269171",
      "name": "Sharon",
      "email": "sharon@apacvebture.com",
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
      "loyaltyPoint": 99,
      "countryCode": "60",
      "phoneNumber": "1126195189",
      "profileImageUrl": "https://storage.googleapis.com/rm-sandbox-asset/img/avatar.png",
      "memberTier": null,
      "status": "ACTIVE",
      "createdAt": "2018-09-13T09:17:24Z"
    },
    {
      "id": "2777058682717858418",
      "name": "yussuf",
      "email": "yussuf@gmail.com",
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
      "loyaltyPoint": 400,
      "countryCode": "60",
      "phoneNumber": "176473298",
      "profileImageUrl": "https://storage.googleapis.com/rm-dev-asset/img/avatar.png",
      "memberTier": null,
      "status": "ACTIVE",
      "createdAt": "2018-09-26T07:13:13Z"
    }
  ],
  "code": "SUCCESS",
  "meta": {
    "count": 3
  }
}
```

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
{ 
   <br>
   <br>
   <br> 
}
</strong>
</aside>



<!--=============--->
<!----Loyalty Member---->
<!--=============---->
##Get Loyalty Member
**Method <span style="color:Green" , bold >`Get`</span>** 

>Example Request

```json
curl --location --request GET "https://sb-open.revenuemonster.my/v3/loyalty/member/2940921291529816182" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{

}"
```

<code>https://sb-open.revenuemonster.my/v3/loyalty/member/2940921291529816182</code>

> Example Respond 

```json
{
  "item": {
    "id": "2940921291529816182",
    "name": "Gan",
    "email": "junkai@revenuemonster.my",
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
    "countryCode": "60",
    "phoneNumber": "167367171",
    "profileImageUrl": "https://storage.googleapis.com/rm-sandbox-asset/img/avatar.png",
    "memberTier": null,
    "status": "ACTIVE",
    "createdAt": "2018-09-19T10:00:21Z"
  },
  "code": "SUCCESS"
}
```

<h3>headers</h3>
| |  |
--------- | ------- |
Content-Type | application/json | 
Authorization | Bearer <br>eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1Nywi<br>aXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1<br>lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.<br>dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw |
X-Signature |sha256 <br> Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==  |
X-Nonce-Str | VYNknZohxwicZMaWbNdBKUrnrxDtaRhN | 
X-Timestamp | 1528450585| 

<h3>Body</h3>

<aside> 
<strong>
{ 
   <br>
   <br>
   <br> 
}
</strong>
</aside>


<!--===============================--->
<!----Loyalty Member Point History---->
<!--===============================---->
##Get Loyalty Member Point History
**Method <span style="color:Green" , bold >`Get`</span>** 

<code>https://sb-open.revenuemonster.my/v3/loyalty/member/2940921291529816182/history</code>


>Example Request

```json
curl --location --request GET "https://sb-open.revenuemonster.my/v3/loyalty/member/2940921291529816182/history" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{

}"
```

>Example Respond 

```json
{
  "items": [
    {
      "key": "EhIKBk1lbWJlchD2kJLw04qQ6CgSGQoNTWVtYmVyUHJvZmlsZRDFjJ-q6rzOxi8SGgoOTG95YWx0eUhpc3RvcnkQs7zyjL79rLIh",
      "type": "POINT_EXPIRED",
      "description": "99 loyalty points expired",
      "point": -99,
      "PointBalance": 0,
      "createdAt": "2018-09-19T16:00:00Z",
      "updatedAt": "0004-04-04T04:04:04Z"
    },
    {
      "key": "EhIKBk1lbWJlchD2kJLw04qQ6CgSGQoNTWVtYmVyUHJvZmlsZRDFjJ-q6rzOxi8SGgoOTG95YWx0eUhpc3RvcnkQ5dH4usjY7coe",
      "type": "VOUCHER_REDEEM",
      "description": "Redeemed voucher",
      "point": 0,
      "PointBalance": 99,
      "createdAt": "2018-09-19T10:01:02Z",
      "updatedAt": "0001-01-01T00:00:00Z"
    },
    {
      "key": "EhIKBk1lbWJlchD2kJLw04qQ6CgSGQoNTWVtYmVyUHJvZmlsZRDFjJ-q6rzOxi8SGgoOTG95YWx0eUhpc3RvcnkQmtaHztvlwqUW",
      "type": "VOUCHER_REDEEM",
      "description": "Discount for Apple Product voucher redeemed",
      "point": -1,
      "PointBalance": 99,
      "createdAt": "2018-09-19T10:00:37Z",
      "updatedAt": "2018-09-19T10:00:37Z"
    },
    {
      "key": "EhIKBk1lbWJlchD2kJLw04qQ6CgSGQoNTWVtYmVyUHJvZmlsZRDFjJ-q6rzOxi8SGgoOTG95YWx0eUhpc3RvcnkQzYCj3ofay5YO",
      "type": "QR_CODE_REDEEM",
      "description": "Earned 100 points",
      "point": 100,
      "PointBalance": 100,
      "createdAt": "2018-09-19T10:00:21Z",
      "updatedAt": "2018-09-19T10:00:21Z"
    }
  ],
  "code": "SUCCESS",
  "meta": {
    "count": 4
  }
}
```

<h3>headers</h3>
| |  |
--------- | ------- |
Content-Type | application/json | 
Authorization | Bearer <br>eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1Nywi<br>aXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1<br>lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.<br>dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw |
X-Signature |sha256 <br> Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==  |
X-Nonce-Str | VYNknZohxwicZMaWbNdBKUrnrxDtaRhN | 
X-Timestamp | 1528450585| 

<h3>Body</h3>

<aside> 
<strong>
{ 
   <br>
   <br>
   <br> 
}
</strong>
</aside>

<!--===============================--->
<!----Bulk Create Members---->
<!--===============================---->
##Post Bulk Create Members
**Method <span style="color:Orange" , bold >`Post`</span>**

> Example Request

```json
curl --location --request GET "https://sb-open.revenuemonster.my/v3/loyalty/member/2940921291529816182" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1NywiaXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw" \
  --header "X-Signature: sha256 Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==" \
  --header "X-Nonce-Str: VYNknZohxwicZMaWbNdBKUrnrxDtaRhN" \
  --header "X-Timestamp: 1528450585" \
  --data "{

}"
```

<code>https://sb-open.revenuemonster.my/v3/loyalty/members</code>

<h3>headers</h3>
| |  |
--------- | ------- |
Content-Type | application/json | 
Authorization | Bearer <br>eyJhbGciOiJSUzI1NiIsImtpZCI6IjIwMTgtMDMtMTMiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOlsiKiJdLCJleHAiOjE1MjE2MjkyNTYsImlhdCI6MTUyMTYyMjA1Nywi<br>aXNzIjoiaHR0cHM6Ly9zYi1vYXV0aC5yZXZlbnVlbW9uc3Rlci5teSIsImp0aSI6IkVod0tFRTlCZFhSb1FXTmpaWE56Vkc5clpXNFF5cmYza3EzTDY4QnoiLCJuYmYiOjE1MjE2MjIwNTcsInN1YiI6IkVoUUtDRTFsY21Ob1<br>lXNTBFSlhWemQzd3JhcVRPUklRQ2dSVmMyVnlFSXlKcUl6dnlNUFZjUSJ9.<br>dJknY9MZHLNrKx1p7gZxS0_oA3uXLWplDU1r1dpwxIbmdB6yw4tQBTXKlWArDfKLlBDn6v22_gT5Px7sdCMj7e5M9eRoJoMnoPnslgYpmJJ5kjqAbKU7dUxKb1OzFLrvmtSK9r-FRLVtMFHioWYpwgSvSPBgZ6lAYkUyDzH7aKadFYtQcBuJR0hlq2CXtP0mzbHOeu2q6giONf3E5-XqS8lLRtuHPAbJ7_YFwo0Oe2zc6h05IOocmx_NvBVPfDBnuygTU063h70Q987MYeGDV_Os4N6N_I4b-GoHprEPtmntB1RJPrFrY28hvvoUfDHXHZVXT1GlrsozrkWV4EjbTw |
X-Signature |sha256 <br> Sty3LNcKA8+WlMHtAgIY+y1xbwnzKsN0UdyKaW+yYIgcTkBAtF7G5Lx251qQITURJ4wiXPDODxhs1nFVmBBing==  |
X-Nonce-Str | VYNknZohxwicZMaWbNdBKUrnrxDtaRhN | 
X-Timestamp | 1528450585| 

>Example Respond 

```json
{
  "item": {
    "id": "2940921291529816182",
    "name": "Gan",
    "email": "junkai@revenuemonster.my",
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
    "countryCode": "60",
    "phoneNumber": "167367171",
    "profileImageUrl": "https://storage.googleapis.com/rm-sandbox-asset/img/avatar.png",
    "memberTier": null,
    "status": "ACTIVE",
    "createdAt": "2018-09-19T10:00:21Z"
  },
  "code": "SUCCESS"
}
```

<h3>Body</h3>

<aside> 
<strong>
{ 
   <br>
   <br>
   <br> 
}
</strong>
</aside>

<!--===============================--->
<!----Bulk register Loyalty Members --->
<!--===============================---->
##Post Bulk register Loyalty Members
**Method <span style="color:Orange" , bold >`Post`</span>**

<code>https://sb-open.revenuemonster.my/v3/loyalty/members</code>

>Example Request

```json
curl --location --request POST "https://sb-open.revenuemonster.my/v3/loyalty/members" \
  --header "Content-Type: application/json" \
  --data "[
	{
		\"name\": \"zhengyan peh\",
		\"countryCode\": \"60\",
		\"phoneNumber\": \"149669976\",
		\"nric\": \"970503145887\",
		\"gender\": \"MALE\",
		\"state\": \"\",
		\"address\": {
			\"addressLine1\": \"\",
			\"addressLine2\": \"\",
			\"postcode\": \"52100\",
			\"city\": \"\",
			\"country\": \"\"
		}
	}
]"
```
<h3>Headers</h3>
| |  |
--------- | ------- |
Content-Type | application/json | 

<h3>Body</h3>

<aside> 
<strong>
{ <br>
	"name": "zhengyan peh", <br>
	"countryCode": "60",<br>
	"phoneNumber": "149669976",<br>
	"nric": "970503145887",<br>
	"gender": "MALE",<br>
	"state": "",<br>
	"address": {<br>
		"addressLine1": "",<br>
		"addressLine2": "",<br>
		"postcode": "52100",<br>
		"city": "",<br>
		"country": ""<br>
	}<br>
}
</strong>
</aside>