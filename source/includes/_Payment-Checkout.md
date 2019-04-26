#Payment-Checkout

*This feature is in Beta mode. Developers will be able to start development in sandbox environment. Please contact us at dev@revenuemonster.my if you would like to be a beta tester.

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

To create a unified payment checkout page for your website.

***REQUEST***

<strong>Request Parameters:</strong>

Parameter | Type | Required | Description | Example
--------- | ------- | ----------- | --- | ---
<code>order</code> | Object | Yes | Object of order | (Refer to explanation below)
<code>method</code> | []String | Yes | Wallet provider for payment, currently supports "WECHATPAY" | ["WECHATPAY_MY"]
<code>type</code> | String | Yes | "STATIC" (for permanent use) or "DYNAMIC" (for one-time use) | "STATIC"
<code>storeId</code> | String | Yes | ID of the store to create QR code | "10946114768247530"
<code>redirectUrl</code> | String | Yes | URL to redirect after payment is made | "https://google.com"
<code>notifyUrl</code> | String | Yes | This is a notify URL or callback URL to inform server on transaction status after payment made. | "https://google.com"

<strong>Order object (`"order"`):</strong>

Parameter | Type | Required | Description | Example
--------- | ------- | ----------- | --- | ---
<code>title</code> | String | Yes | Order title, max: 32 | "Sales"
<code>detail</code> | String | Yes | Order detail, max: 600 | "1 x iPhone X; 2 x SAMSUNG S8"
<code>additionalData</code> | String | Yes | Order description | "Sales"
<code>amount</code> | Uint | Yes |  Amount of order in cent. Only required when "isPrefillAmount" = true. (min RM 0.10 or amount: 10) | 100
<code>currencyType</code> | String | Yes | Currency notation (currently only support `MYR`) | "MYR"
<code>id</code> | String | Order ID | "6170506694335521334"


***RESPONSE***

<strong>Response Parameters:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>items</code> | Object | item object | (Refer to explanation below)
<code>code</code> | String | Successfully call this endpoint. If fail, will return error code object (Refer `Appendix 1: Error Codes`) | "SUCCESS"

<strong>`"item"` Object:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>code</code> | String | Code to identify web payment url | "1547775958720585401"
<code>url</code> | String | Example to form checkout URL. Note: to change base URL to desired URL. | "http://localhost:8081/checkout?code=1547775958720585401"

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

