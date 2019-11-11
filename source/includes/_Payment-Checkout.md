#Payment-Web/App Checkout

Scenarios:

1. E-commerce website payment checkout.

To make payment with a unified payment checkout page.

- Scope: `manage_payment`
- Authentication: Access token obtained from [Generate Access Token](https://doc.revenuemonster.my/#66368026-71ee-4640-8ad7-208f843c6d6c) into `Authorization` header value as `Bearer [access_token]`.

<!--======================--->
<!--Create Transaction Web or Mobile Payment--->
<!--======================--->

##Create Transaction Web or Mobile Payment
**Method <span style="color:Orange" , bold >`POST`</span>**

<code>https://sb-open.revenuemonster.my/v3/payment/online</code>

To create a unified payment checkout page for your website and Mobile

- Demo web payment: [Click Here](https://sb-api.revenuemonster.my/demo/payment/online)

**_REQUEST_**

<strong>Request Parameters:</strong>

| Parameter                  | Type     | Required | Description                                                                                                                                                   | Example                                                               |
| -------------------------- | -------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| <code>order</code>         | Object   | Yes      | Object of order                                                                                                                                               | (Refer to explanation below)                                          |
| <code>method</code>        | []String | Yes      | Wallet provider for payment, currently supports "WECHATPAY MY", "WECHATPAY CN", "Presto", "Boost","ALIPAY_CN" , "GRABPAY_MY",("TNG_MY" **For Sandbox Only**). | ["WECHATPAY_MY","WECHATPAY_CN" <br/>,"PRESTO_MY","BOOST_MY","TNG_MY"] |
| <code>type</code>          | String   | Yes      | Obejct of type                                                                                                                                                | (Refer to explanation below)                                          |
| <code>storeId</code>       | String   | Yes      | ID of the store to create QR code                                                                                                                             | "10946114768247530"                                                   |
| <code>redirectUrl</code>   | String   | Yes      | URL to redirect after payment is made                                                                                                                         | "https://google.com"                                                  |
| <code>notifyUrl</code>     | String   | Yes      | This is a notify URL or callback URL to inform server on transaction status after payment made.                                                               | "https://google.com"                                                  |
| <code>layoutVersion</code> | String   | Optional | New layout for Web paymnet                                                                                                                                    | v1                                                                    |

> Example Request

```json
curl --location --request POST "{{open_base_path}}/v3/payment/online" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer {{clientToken}}" \
  --header "X-Nonce-Str: XAYZRZNLGCKSTURRFKBIGYALUKLCLJOG" \
  --header "X-Signature: sha256 YTTV0p1XJUllLNwAC/m430ZbteZhdBmUm3aVnKH4XEZU2yfl7liCPzEI40VqTwFcmMLByJ0mRyzc97gzVn1XZVIr1DaPpW3LUv/on82hIDhLue4uJzKg+vS8/CKJC4+SJ1NpL4rDQEg/hdq4mrNIckTN5+UCFbM4tLCDN8FanSoI3SxcfmvfBwuOc5ro4WWStJlr/LxLJWHRdI8ZpTc1gmNkzRKA9YXJI6iACrkg4cUtMkQ0nii9dHu+brKtK2gCtZ6kdPxgiykDlJuPcpHBGsG+wjNGXLxNeeZjbIl6m40dtdwwyiDbdsk/ZelN0J8Xw1rti7a7dHY/vNnN4W+tUA==" \
  --header "X-Timestamp: 1547643342" \
  --data "{
    \"order\": {
    	\"title\": \"hello\",
    	\"detail\": \"hello\",
    	\"additionalData\": \"world\",
	    \"amount\": 100,
	    \"currencyType\": \"MYR\",
	    \"id\": \"13234353336\"
    },
    \"method\": [],
    \"type\": \"WEB_PAYMENT\",
    \"storeId\": \"977596145540933417\",
    \"redirectUrl\": \"https://google.com\",
    \"notifyUrl\": \"https://google.com\",
    \"layoutVersion\": \"v1\"
}"
```

<strong>Order object (`"order"`):</strong>

| Parameter                   | Type   | Required | Description                                                                                       | Example                        |
| --------------------------- | ------ | -------- | ------------------------------------------------------------------------------------------------- | ------------------------------ |
| <code>title</code>          | String | Yes      | Order title, max: 32                                                                              | "Sales"                        |
| <code>detail</code>         | String | Yes      | Order detail, max: 600                                                                            | "1 x iPhone X; 2 x SAMSUNG S8" |
| <code>additionalData</code> | String | Yes      | Order description                                                                                 | "Sales"                        |
| <code>amount</code>         | Uint   | Yes      | Amount of order in cent. Only required when "isPrefillAmount" = true. (min RM 0.10 or amount: 10) | 100                            |
| <code>currencyType</code>   | String | Yes      | Currency notation (currently only support `MYR`)                                                  | "MYR"                          |
| <code>id</code>             | String | Order ID | "6170506694335521334"                                                                             |

<strong>Type Object (`"type"`):</strong> <br/>

| Parameter         | Type   | Required | Description                                                                                                                                                     | Example          |
| ----------------- | ------ | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| <code>type</code> | String | Yes      | "WEB_PAYMENT" (Currenty for Web payment only support <strong>"WECHATPAY_MY","WECHATPAY_CN" <br/>,"PRESTO_MY","BOOST_MY",<br/>"ALIPAY_CN","GRABPAY_MY"</strong>) | "WEB_PAYMENT"    |
| <code>type</code> | String | Yes      | "MOBILE_PAYMENT" (Currenty for Mobile payment only support <strong><br/>"WECHATPAY_MY","BOOST_MY"</strong>)                                                     | "MOBILE_PAYMENT" |

> Example Respond

```json
{
  "item": {
    "checkoutId": "1548316308361173347",
    "url": "https://sb-pg.revenuemonster.my/checkout?checkoutId=1548316308361173347"
  },
  "code": "SUCCESS"
}
```

**_RESPONSE_**

<strong>Response Parameters:</strong>

| Parameter          | Type   | Description                                                                                               | Example                      |
| ------------------ | ------ | --------------------------------------------------------------------------------------------------------- | ---------------------------- |
| <code>items</code> | Object | item object                                                                                               | (Refer to explanation below) |
| <code>code</code>  | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"                    |

<strong>`"item"` Object:</strong>

| Parameter         | Type   | Description                                                            | Example                                                   |
| ----------------- | ------ | ---------------------------------------------------------------------- | --------------------------------------------------------- |
| <code>code</code> | String | Code to identify web payment url                                       | "1547775958720585401"                                     |
| <code>url</code>  | String | Example to form checkout URL. Note: to change base URL to desired URL. | "http://localhost:8081/checkout?code=1547775958720585401" |

<strong>Example of Notify URL Response</strong>

<aside class="success"> <strong>Example :</strong>
<br>
<strong>
{ <br>
  "data":{  <br>
      "balanceAmount":100,<br>
      "createdAt":"2019-03-01T05:51:20Z",<br>
      "currencyType":"MYR",<br>
      "method":"WECHATPAY",<br>
      "order":{  
         "additionalData":"Payment to 11street",<br>
         "amount":100,<br>
         "detail":"Payment to 11street",<br>
         "id":"P000000660800",<br>
         "title":"Payment to 11street"<br>
      },<br>
      "payee":{  
         "userId":"oKz050cwbEJwKAnKZgbD24UYibHQ"
      },<br>
      "platform":"OPEN_API",<br>
      "referenceId":"1010014200000026201903016100904600",<br>
      "region":"MALAYSIA",<br>
      "status":"SUCCESS",<br>
      "store":{  <br>
         "addressLine1":"",<br>
         "addressLine2":"",<br>
         "city":"",<br>
         "country":""<br>,
         "countryCode":"",<br>
         "createdAt":"2018-10-02T10:52:03Z",<br>
         "geoLocation":{ <br> 
            "latitude":0,<br>
            "longitude":0<br>
         },<br>
         "id":"2551293210619662240",<br>
         "imageUrl":"https://storage.googleapis.com/rm-prod-asset/img/store.png",<br>
         "name":"11Street",<br>
         "phoneNumber":"",<br>
         "postCode":"",<br>
         "state":"",<br>
         "status":"ACTIVE",<br>
         "updatedAt":"2018-10-02T10:52:03Z"<br>
      },<br>
      "terminalId":"",
      "transactionAt":"2019-03-01T05:51:59Z",<br>
      "transactionId":"190301055133300427675601",<br>
      "type":"WEB_PAYMENT",<br>
      "updatedAt":"2019-03-01T05:52:00.897920132Z",<br>
      "voucher":null <br>
   },<br>
   "eventType":"PAYMENT_WEB_ONLINE"
}
</strong>
</aside>

![images](images/webpayment.png)
![images](images/webpayment-1.png)

<!--======================--->
<!--Get Individual QR Code --->
<!--======================--->

##Get Individual QR Code
**Method <span style="color:Green" , bold >`Get`</span>**

<code>https://sb-open.revenuemonster.my/v3/payment/online/qrcode?checkoutId=1561390635417535731&method=WECHATPAY_MY</code>

**_REQUEST_**

<strong>Request Parameters:</strong>

| Parameter               | Type   | Description                                                                                                                  | Example               |
| ----------------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------- | --------------------- |
| <code>checkoutId</code> | String | Code to identify web payment url                                                                                             | "1547775958720585401" |
| <code>method</code>     | String | Wallet provider for payment, currently supports "WECHATPAY MY ","WECHATPAY CN","Presto", "Boost","ALIPAY_CN" , "GRABPAY_MY". | ["WECHATPAY_MY"]      |

> Example Request

```json
curl --location --request GET "{{open_base_path}}/v3/payment/online/qrcode?checkoutId=1559485554334807004&method=BOOST_MY" \
  --header "Content-Type: application/json" \
  --header "Authorization: Bearer {{clientToken}}" \
  --header "X-Nonce-Str: XAYZRZNLGCKSTURRFKBIGYALUKLCLJOG" \
  --header "X-Signature: sha256 RLHmhe9pvCnM6wbp2UcQcyyjBXKbVhlbshaZqUBdgxqdnbM6WsmQuQL1PwhsF6/uOxoXtoXaLIi18zN0IQp5MdxNSiq+6MPLZqmPpiWyJSXpzZsUVst43tKp+JZDF8AWXesrol5vj1RVbxOvCfnkmfghA83mlKc4scXIJkqXpFdyKcRmjT6Bsu9nlMh5IdyBSKv3goatgso/4IsEi8R220ZSHp2Ai//g9iKrKG3cgspM2Uj74ZXIrzt8IB+660btXyoanMuqgqirl1ulj59KciqLKqQMYoHfRywJTH0XLDtV1fQHO1FAECwmMd91Y63acnH3BOxo023tF7AXwNASsg==" \
  --header "X-Timestamp: 1547643342"
```

**_RESPONSE_**

<strong>Response Parameters:</strong>

> Example Respond

```json
{
  "item": {
    "qrCodeImageBase64": "iVBORw0KGgoAAAANSUhEUgAAAQAAAAEACAMAAABrrFhUAAAABlBMVEX///8AAABVwtN+AAADOUlEQVR42uzdwW7bOhAF0Pj/f/ot3yZm7iWHaWCdu2oRC5BOAGo8Q7ZfIiIiIiIiIiIiIiIi8vo5b6/4/6/rj7y97LuPfHdXm3cKAAAAABlA+tP1Q7xFWX8ufYiTnwIAAADAjxe+XXnTxX79OJtvgf5OAQAAAOAWQMXz9rLgDt7+FAAAAAD+BMD6svX396DSPvllAAAAAMCFfkD6tT+lTV8U6SMCAAAAwNXJ0B/5078bjQEAAOAzAU5K5qAUTgdA1+8fAAAAALp+wPEeoaqx2fdXp9Z+AAAAPBsgXefTBwu+51cNhaBAn1IAAADAEwHS3Y3BR04q3uq9sX4tAQAAAMCF5fBEK91B2c/cR3sJAAAAeCJA0OzsewnpkL06WhO0BwAAAADgcCU86Wn299Cv5JdGSwAAAADwqp4uWNjTfd7BO+dmFwAAAADPBqjalNUpwHQRT5+kP7QIAAAAABeq4H5drg4jpj2CqYYwAAAAALz644H9JKcvhYNrR88MAQAA4IkAa5Sq9q0m2X2lPb8hAAAAAAC6LYn9hDp9nKrE3WwoAAAAAEDbGejvq9pLWQ3Ag18aAAAAAExMhtJpeXWqJt2Mno7b53eKAgAA4IkAfYmb7lU82fsYtEJ/uyECAACAzwQYPN237psGa3oqc7MhAgAAgIcBpEXs9JpeDY/mz8gAAAAAwNfmSp7ibXpM/0YAAAAAYKserorYqu0ZNDZvbg8HAAAAgKEOZdWw3NwoXp3SBgAAAIDZerjatd0X1OkpmOowIgAAAADsV8EVVFDnpn3O484AAAAAAMxulDx54mqZTrcbXdoeCQAAAADxN/l+iT8psn9ntyQAAAAAxP+/QHBfad0c1MPpBGl+pygAAACeA7BZMvenCk8G70EPFwAAAABeU0OhapLdt0zTidRmHwIAAAAADpui625BOqtO69x+0j6/XR4AAAAANorToBqtJuObu8rnGyIAAAAA0G0ASmWCWroaKI2WwgAAAAAQf51PnySoudMl/lIbGAAAAAB2/yX/dACU7umphuxTu4UAAAAAYGi6Hbwjqg7C+nZH5/4AAAB4LICIiIiIiIiIiIiIiIh8Vv4LAAD//+flU07X8QYtAAAAAElFTkSuQmCC",
    "url": "https://mywallet.wechatpay.com.my/app/pay/myw_order_idx.cgi?prepay_id=415613907510f1b0e0920320010983"
  },
  "code": "SUCCESS"
}
```

**Example of the Indvidual QR Code**

Decoder Base64 to Image <br/>

<code>iVBORw0KGgoAAAANSUhEUgAAAQAAAAEACAMAAABrrFhUAAAABlBMVEX///8AAABVwtN+AAADOUlEQVR42uzdwW7bOhAF0Pj/f/ot3yZm7iWHaWCdu2oRC5BOAGo8Q7ZfIiIiIiIiIiIiIiIi8vo5b6/4/6/rj7y97LuPfHdXm3cKAAAAABlA+tP1Q7xFWX8ufYiTnwIAAADAjxe+XXnTxX79OJtvgf5OAQAAAOAWQMXz9rLgDt7+FAAAAAD+BMD6svX396DSPvllAAAAAMCFfkD6tT+lTV8U6SMCAAAAwNXJ0B/5078bjQEAAOAzAU5K5qAUTgdA1+8fAAAAALp+wPEeoaqx2fdXp9Z+AAAAPBsgXefTBwu+51cNhaBAn1IAAADAEwHS3Y3BR04q3uq9sX4tAQAAAMCF5fBEK91B2c/cR3sJAAAAeCJA0OzsewnpkL06WhO0BwAAAADgcCU86Wn299Cv5JdGSwAAAADwqp4uWNjTfd7BO+dmFwAAAADPBqjalNUpwHQRT5+kP7QIAAAAABeq4H5drg4jpj2CqYYwAAAAALz644H9JKcvhYNrR88MAQAA4IkAa5Sq9q0m2X2lPb8hAAAAAAC6LYn9hDp9nKrE3WwoAAAAAEDbGejvq9pLWQ3Ag18aAAAAAExMhtJpeXWqJt2Mno7b53eKAgAA4IkAfYmb7lU82fsYtEJ/uyECAACAzwQYPN237psGa3oqc7MhAgAAgIcBpEXs9JpeDY/mz8gAAAAAwNfmSp7ibXpM/0YAAAAAYKserorYqu0ZNDZvbg8HAAAAgKEOZdWw3NwoXp3SBgAAAIDZerjatd0X1OkpmOowIgAAAADsV8EVVFDnpn3O484AAAAAAMxulDx54mqZTrcbXdoeCQAAAADxN/l+iT8psn9ntyQAAAAAxP+/QHBfad0c1MPpBGl+pygAAACeA7BZMvenCk8G70EPFwAAAABeU0OhapLdt0zTidRmHwIAAAAADpui625BOqtO69x+0j6/XR4AAAAANorToBqtJuObu8rnGyIAAAAA0G0ASmWCWroaKI2WwgAAAAAQf51PnySoudMl/lIbGAAAAAB2/yX/dACU7umphuxTu4UAAAAAYGi6Hbwjqg7C+nZH5/4AAAB4LICIiIiIiIiIiIiIiIh8Vv4LAAD//+flU07X8QYtAAAAAElFTkSuQmCC</code>

![images](images/individualQRcode.png) <br/> <br/>
![images](images/paymentCheckOut.png)
