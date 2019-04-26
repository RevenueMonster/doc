#Appendix 1: Error Codes

| Error Codes | Description | Solution |
| --- | --- | --- | 
| InvalidRequest:      |    The request is missing a required parameter, includes an invalid parameter value, includes a parameter more than once, or is otherwise malformed. | Refer to request paramenter(s) as described in API documentation and retry again. |
| InvalidGrant:        |    Invalid grant | Check redirect URI (must be exactly the same as request URI query string) |
| InvalidClient:       |    Invalid client | Client is not registered in our system, please try again with correct clientId, clientSecret. | 
| InvalidCode:        |     Invalid authorization code | This is not the correct authorization code generated from our system, please request a new authorization code again. |
| InActiveClient:       |   Client mode is inactive | This client/application is disabled, login to Merchant Portal and reactivate it. |
| InvalidScope:       |     The requested scope is invalid, unknown, or malformed. | 1. Check scope, currently only support `manage_payment`, `manage_store`, `get_merchant_profile`, `get_user_profile`. 2. Check scope of this user, requested scope cannot be greater than user scope in our system. |
| UnAuthorizedClient:   |   The client is not authorized to request this method. | Use other client to request this method. |
| UnSupportedGrantType:  |  Unsupported grant type | Currently we only support grant types of `Client Credentials`, `Authorization Code` and `Refresh Token`. |
| UnSupportedResponseType: | The authorization server does not support obtaining an authorization code using this method.  | Use `responseType=code` in request URI query string and try again. |
| AccessDenied:      |      The resource owner or authorization server denied the request | User is inactivated in our system, please try again. |
| InternalError:     |      The authorization server encountered an unexpected condition that prevented it from fulfilling the request | Should this condition presists, please contact our customer support. |
| TemporaryUnAvailable:  |  The authorization server is currently unable to handle the request due to a temporary overloading or maintenance of the server | Should this condition presists, please contact our customer support. |

##Appedix: Version Control

- 11/06/2018: Updated RSA keys generator, improved documentation description in RM OAuth, updated Signature Debugger, updated each endpoint structure.
- 01/07/2018: Added "Payment Transaction QR Code" endpoint(s).
- 16/07/2018: Refactor documentation for Signature Algorithm.
- 30/07/2018: Removed `isDebug` parameter in all API calls. Added `terminalId` for payment API.
