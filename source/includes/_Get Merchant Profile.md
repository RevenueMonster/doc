##Get Merchant Profile 
**Method <span style="color:Green" , bold >`GET`</span>**

To query for merchant details.

***REQUEST***

<strong>Request Parameters:</strong>

*Note: No request parameter is required for this endpoint*

Eg. Plain text parameters:
`method=get&nonceStr=VYNknZohxwicZMaWbNdBKUrnrxDtaRhN&requestUrl=https://sb-open.revenuemonster.my/v3/merchant&signType=sha256&timestamp=1527407052`


***RESPONSE***

<strong>Response Parameters:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>item</code> | Object | Object of refund details. | (Refer explanantion below)
<code>code</code> | String | Status returned from Revenue Monster server, whether successfully called our endpoint or not. | "SUCCESS"

<strong>Item Object:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>id</code> | String | Store ID | "6170506694335521334"
<code>companyName</code> | String | Company name of merchant | "REVENUE MONSTER"
<code>companyType</code> | String | Type of company incorporation | "SOLE PROPRIETOR"
<code>companyLogoUrl</code> | String | Public URL to show merchant's logo | "https://storage.googleapis.com/rm-dev-asset/img/merchant.png"
<code>registrationNumber</code> | String | Registration number of merchant  | “12344”
<code>businessCategory</code> | String | Business category of merchant | "SOFTWARE AND IT"
<code>establishedAt</code> | String | Established date time of merchant | "2018-03-26T04:50:57Z"
<code>countryCode</code> | String | Country code of merchant contact number | "60"
<code>phoneNumber</code> | String | Phone number of merchant | "377334080"
<code>addressLine1</code> | String | Address 1 of merchant | "20, JALAN JASA 38, TAMAN MUTIARA RINI"
<code>addressLine2</code> | String | Address 2 of merchant | ""
<code>postcode</code> | String | Postcode of merchant | “81300”
<code>city</code> | String | City of merchant | "Selangor"
<code>state</code> | String | State of merchant | "Selangor"
<code>country</code> | String | Country of merchant | "Malaysia"
<code>invoiceAddres</code> | Object | Object of Invoice Address | (Refer below)
<code>isActive</code> | Boolean | Merchant active or deactivated status | true
<code>status</code> | String | Current status of merchant | “REVIEWING”
<code>isMasterMerchant</code> | Bool | Master Merchant flag | true
<code>masterMerchantId</code> | String | Master Merchant ID, if any | "2301663653361832803"
<code>isPartner</code> | Bool | Partner Merchant flag | true
<code>partnerId</code> | String | Partner Merchant ID, if any | "2301663653361832803"
<code>gstNo</code> | String | GST No, if any | ""
<code>createdAt</code> | DateTime | Creation date time of merchant | "2018-02-12T08:53:13Z"
<code>updatedAt</code> | DateTime | Last update date time of merchant | "2018-02-12T08:53:13Z"

<strong>Invoice Address Object:</strong>

Parameter | Type | Description | Example
--------- | ------- | ----------- | ---
<code>addressLine1</code> | String | Address 1 of merchant | "20, JALAN JASA 38, TAMAN MUTIARA RINI"
<code>addressLine2</code> | String | Address 2 of merchant | ""
<code>postcode</code> | String | Postcode of merchant | “81300”
<code>city</code> | String | City of merchant | "Selangor"
<code>state</code> | String | State of merchant | "Selangor"
<code>country</code> | String | Country of merchant | "Malaysia"