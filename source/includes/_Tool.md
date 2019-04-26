#Tool

##Post Verify Signature 
**Method <span style="color:Orange" , bold >`POST`</span>**

`https://sb-open.revenuemonster.my/tool/signature/verify`

>Example Request

```json
curl --location --request POST "https://sb-open.revenuemonster.my/tool/signature/verify" \
  --header "Content-Type: application/json" \
  --data "{
	\"data\": {
		\"test\": \"world\"
	},
	\"method\": \"post\",
	\"nonceStr\": \"VYNknZohxwicZMaWbNdBKUrnrxDtaRhN\",
	\"publicKey\": \"-----BEGIN PUBLIC KEY-----\
MFswDQYJKoZIhvcNAQEBBQADSgAwRwJAbbPqIDbm4/b4IcyH5TgG6y5PS4YNZYZH\
ULZRYONqBWYAtkuy7nzQ3zn/HOBF8RHwf37cMbzOInSr+Exoh1KfnwIDAQAB\
-----END PUBLIC KEY-----\",
	\"requestUrl\": \"https://open.localhost:8080/v3/stores\",
	\"signType\": \"sha256\",
	\"timestamp\": \"1527407052\",
	\"signature\": \"Whm4Ud2XCcxspqNJLKc+FlH7U2JVP6lafCYO3+KMxSf9CI6IYdu5eCwjvA4CMm9+O9A1+XEATOjBODvDlgoG5A==\"
}"
```



<h3>Headers</h3>
 | |  
--------- | ------- |
Content-Type | application/json | 

>Example Respond

```json
{
  "isValid": true
}
```

<h3>Body</h3>

<aside> 
<strong>
{<br>
 <br>"data": {},
 <br>"method": "post",
 <br>"nonceStr": "VYNknZohxwicZMaWbNdBKUrnrxDtaRhN",
 <br>"publicKey": "-----BEGIN RSA PUBLIC KEY-----MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAq1+AThD/2f8qsDP2luyHyffBPvdR1HrOWHyZR5iQ2prcr0l4MD<br>lbYqQ4+8mArdhM1fRMblse1tpS7UvKcZQKHkxhl0eZcJd7EoPSUC5GdFXiTXTC3y<br>l7wfBWul5pRZglS0009zoQs+jv2wrQbnc6RgCkTZyzw93w/FbL5zMvXRnfbIxmQU7FfdpWQrqX/<br>lHjM7PcVd9XZy46KwizuhrybxCDYqpLbcrlljUqG8Upqq4FKn86a/EbYk41cx39fbNRkCxrQ0bv+/<br>Nkd2iDIHBIYx0alQ6DmAC41hpKwzHmzWEl3dS86huSJF7eZ6flqaTbhH52A1nZuiGEEjq6P0/XIQIDAQAB<br>-----END RSA PUBLIC KEY-----",
 <br>"requestUrl": "https://open.localhost:8080/v3/store",
 <br>"signType": "sha256",
 <br>"timestamp": "1527407052",
 <br>"signature": "CJh+mIfiLofRfOBm8bEm/<br>z16TW+r40lV8kzJln+esEN+AU693Sxvo6YxJXJHNI5uXJc3PpuZQQuSPUNLge<br>XBYMmgb3tOKywiBvPhqdzCVMNXKQoFKMdv+Z7a5bumYWAi6K4FnXITBdgf/<br>lIIRN/l9J/<br>nfyJA1bP7n5DDWx4q9ngBQfSOgXAPyyAqQPsMEjapgHq5xd9NSYOA2Cf05pa6MppEgyoesCrRT51a+9RlaaFlm<br>V5EsdKaa5Aw9H8ROiK/<br>EhwNLdfsMainHzeTfApHx8EzvHqd8Rur7KcHMjMaOdhF+uFWdeN1enyrsGPHQ99E22KJpZ0DsZgPampEMr5Maw=="
<br>}
</strong>
</aside>

##Post Generate Signature 
**Method <span style="color:Orange" , bold >`POST`</span>**

`https://sb-open.revenuemonster.my/tool/signature/generate`


>Example Request

```json
curl --location --request POST "https://sb-open.revenuemonster.my/tool/signature/generate" \
  --header "Content-Type: application/json" \
  --data "{
  \"data\": {
\"amount\":100,\"currencyType\":\"MYR\",\"expiry\":{\"type\":\"PERMANENT\"},\"isPreFillAmount\":true,\"method\":[\"WECHATPAY\"],\"order\":{\"detail\":\"detail\",\"title\":\"title\"},\"redirectUrl\":\"https://google.com\",\"storeId\":\"1234\",\"type\":\"DYNAMIC\"
  },
  \"method\": \"post\",
  \"nonceStr\": \"MNhrdDgIDlTKdlYXzfhEvqHpGjRhvrPe\",
  \"privateKey\": \"-----BEGIN RSA PRIVATE KEY-----\
MIICXAIBAAKBgQDD3n2Ux9jdlqQFK/nWiPfounUif0f8pnwIw29q1vWRRCoTACVJ\
fVRZTiFWQnlT0W73OdmH7yMAl7TfJYxchl1cYGwTKjvlBwj7YCLZfLtEhfyRN8MC\
bUS9RKZMDU5peSVHFls9XDiTD8h17Z/ZZcAIf9Me9luvsG4qTa+ffd1AIwIDAQAB\
AoGAJg+S+ZlIA+8k2jhsaQremaO55UU0eNzlF1La0LkKqPrE7kJF/JzVCjGLetaZ\
+vakiHf+VFLcy12vcPk76DLX6ydbgiiA1CCOKnpAnMubKDq/wYLt3OXY19t9QXHo\
vm70lcQM6/IuBs1o3aUjRumJjh0cVcjKKqS5eF6j0AQZGxECQQDpZ+j6/3cdTdLA\
E0niJQBQefIoBUoocWDvs/dt0jta9mrWlYFnEz+CFaY+roF/fcxmmxKF6/2l0DuS\
vGZH0x/bAkEA1tRfLGG/CYv6e4iTE75AtpDeVD3QURfVlLVIKAjjSK2woopK3Hsp\
ocRb+cjL5GZipBM5Q6uCtAj0QZHvsxeXWQJBAJDTagv8YhOry15lWY3Z+bT1xd0x\
Uw9/Mm/p0lixfyT1C9v0TqP/nIOCHXJ9Y1sRWrg79qVkhjHR4HUvM6PTi8sCQB/v\
Jc6lIQ68PhnK7YILz/bThhkjrym+z0Lxx64b1B1jpFQlFoe7zy56z+lLjfN/vL4D\
FYoXnrBAfH6awPTwVtECQC2LIuer+rYpCb8hYsWFksYQOV2rWrwQTXgDhmdRra7L\
+6JZP+MzKwD9vs7Mv+QUbSnisAPqXRCV6giMHmj/Vkc=\
-----END RSA PRIVATE KEY-----\",
  \"requestUrl\": \"https://sb-open.revenuemonster.my/v3/payment/transaction/qrcode\",
  \"signType\": \"sha256\",
  \"timestamp\": \"1532069238\"
}"
```

<h3>Headers</h3>
 | |  
--------- | ------- |
Content-Type | application/json | 

>Example Respond

```json
{
  "data": "data=eyJhbW91bnQiOjEwMCwiY3VycmVuY3lUeXBlIjoiTVlSIiwiZXhwaXJ5Ijp7InR5cGUiOiJQRVJNQU5FTlQifSwiaXNQcmVGaWxsQW1vdW50Ijp0cnVlLCJtZXRob2QiOm51bGwsIm9yZGVyIjp7ImRldGFpbCI6ImRldGFpbCIsInRpdGxlIjoidGl0bGUifSwicmVkaXJlY3RVcmwiOiJodHRwczovL2dvb2dsZS5jb20iLCJzdG9yZUlkIjoiMTIzNCIsInR5cGUiOiJEWU5BTUlDIn0=&method=post&nonceStr=MNhrdDgIDlTKdlYXzfhEvqHpGjRhvrPe&requestUrl=https://sb-open.revenuemonster.my/v3/payment/transaction/qrcode&signType=sha256&timestamp=1532069238",
  "sequenceData": "{\"amount\":100,\"currencyType\":\"MYR\",\"expiry\":{\"type\":\"PERMANENT\"},\"isPreFillAmount\":true,\"method\":null,\"order\":{\"detail\":\"detail\",\"title\":\"title\"},\"redirectUrl\":\"https://google.com\",\"storeId\":\"1234\",\"type\":\"DYNAMIC\"}",
  "signature": "sha256 gCwAhdaHdF4RE7fE9E1mODoEEdd50IcUfFsrxlWvciW+CyFEc/zjmfG9UaNxD7Xmi7cVYbuoUdQGTuXP6VbE6PFgd3t6wWl9ZokBSfYs5260JtBfDdPn263Wz6iTrrPJFQUI60yH4IsDi3uS6FKxP2/hnued4tEiv6pcgZ8o0CY="
}
```

<h3>Body</h3>

<aside> 
<strong>
{<br>
 <br>"data": {},
 <br>"method": "get",
 <br>"nonceStr": "MNhrdDgIDlTKdlYXzfhEvqHpGjRhvrPe",
 <br>"privateKey": "-----BEGIN RSA PRIVATE KEY-----\n<br>MIIBOgIBAAJBALEfYbfkZ1G6zrrHf5Yps1vibzfMwr07J5MEdz/<br>3dvsMk+U/BrkM\nt43laBrd1sadcMaEMsZQ4JR2g8Ml6VQIJ/sCAwEAAQJAdu0/S54M0Y/A5yC0xjrR\nt0xeqPTPfQePFu<br>PUvhqGxSEa5IEvywt12loV4Ja6jPVHVzqMYW0Vt5NonQqVWT4+\n<br>YQIhANcJA8mzd+Oem8vSinX7mPDZjfppCvCJ4yEYS9RJHf1vAiEA0t1q8P7QX0TC\n<br>x3sBbIvonqnEv8a0LO/I4ioZqrhgUDUCIQCOtm3sJI7x4ycU+9NnACb92fUvdx2K\n<br>jIjQQxa4ehpMQwIgPfCigEYpiUKWgKhGQ89ZNnoh/<br>D9vH6AT/zNktLxSNl0CIFou\nC1lV28IhuxqmRP/Ea/HSGj4Cn5ToIUINlRUBkOtB\n<br>-----END RSA PRIVATE KEY-----",
 <br>"requestUrl": "https://open.revenuemonster.my/v3/payment/transaction/qrcode/647384dc63b4c0f3cabb7d7d0b3fa867/<br>transactions",
 <br>"signType": "sha256",
 <br>"timestamp": "1551670378"<br>
}
</strong>
</aside>

