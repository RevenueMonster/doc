#Appendix 1: Error Codes

| Error Codes              | Description      | Solution                                                                                                                                                                                                           |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| InvalidRequest:          | The request is missing a required parameter, includes an invalid parameter value, includes a parameter more than once, or is otherwise malformed. | Refer to request paramenter(s) as described in API documentation and retry again.                                                                                                                                  |
| InvalidGrant:            | Invalid grant                                                                                                                                     | Check redirect URI (must be exactly the same as request URI query string)                                                                                                                                          |
| InvalidClient:           | Invalid client                                                                                                                                    | Client is not registered in our system, please try again with correct clientId, clientSecret.                                                                                                                      |
| InvalidCode:             | Invalid authorization code                                                                                                                        | This is not the correct authorization code generated from our system, please request a new authorization code again.                                                                                               |
| InActiveClient:          | Client mode is inactive                                                                                                                           | This client/application is disabled, login to Merchant Portal and reactivate it.                                                                                                                                   |
| InvalidScope:            | The requested scope is invalid, unknown, or malformed.                                                                                            | 1. Check scope, currently only support `manage_payment`, `manage_store`, `get_merchant_profile`, `get_user_profile`. 2. Check scope of this user, requested scope cannot be greater than user scope in our system. |
| UnAuthorizedClient:      | The client is not authorized to request this method.                                                                                              | Use other client to request this method.                                                                                                                                                                           |
| UnSupportedGrantType:    | Unsupported grant type                                                                                                                            | Currently we only support grant types of `Client Credentials`, `Authorization Code` and `Refresh Token`.                                                                                                           |
| UnSupportedResponseType: | The authorization server does not support obtaining an authorization code using this method.                                                      | Use `responseType=code` in request URI query string and try again.                                                                                                                                                 |
| AccessDenied:            | The resource owner or authorization server denied the request                                                                                     | User is inactivated in our system, please try again.                                                                                                                                                               |
| InternalError:           | The authorization server encountered an unexpected condition that prevented it from fulfilling the request                                        | Should this condition presists, please contact our customer support.                                                                                                                                               |
| TemporaryUnAvailable:    | The authorization server is currently unable to handle the request due to a temporary overloading or maintenance of the server                    | Should this condition presists, please contact our customer support.                                                                                                                                               |

##Error Codes 
|Code| Description | Error Message |
|----------|----------------------------------------------------------------------|---------------|
|AlipayChinaNotActive: | Alipay China is not active. Please contact Revenue Monster to activate merchant for alipay | ALIPAY_CHINA_NOT_ACTIVE |
																								| AccessTokenReadFail: | Cannot read access token file|ACCESS_TOKEN_READ_FAIL|																									
| AccountFrozen: | Your account has been frozen. Please contact support.|ACCOUNT_FROZEN|																									
| AccountInactive: | User account is inactive|ACCOUNT_INACTIVE|																									
| AccountNotFound: | Account does not exist|ACCOUNT_NOT_FOUND|																									
| AccountSuspended: | This account is temporarily locked|ACCOUNT_SUSPENDED|																									
| AgreementAlreadySigned: | Agreement already signed|AGREEMENT_ALREADY_SIGNED|																									
| AgreementNotFound: | Agreement not found|AGREEMENT_NOT_FOUND|																									
| AgreementNotSigned: | Agreement not signed|AGREMENT_NOT_SIGNED|																									
| AccessTokenFail: | Fail to request access token | ACCESS_TOKEN_FAIL |																									
| AliPayClientDuplicate: | Alipay client duplicate|ALIPAY_CLIENT_DUPLICATE|																									
| AlreadyMasterMerchant: | Already master merchant|ALREADY_MASTER_MERCHANT|																									
| APIEndpointNotFound: | The api endpoint does not exist|API_ENDPOINT_NOT_FOUND|																									
| APIInactive: | This API version is no longer active. Please migrate to API v3|API_INACTIVE|																									
| AuthCodeExpired: | Customer code expired. Please scan again.|AUTH_CODE_EXPIRED|																									
| AuthCodeInvalid: | Customer code expired. Please scan again.|AUTH_CODE_INVALID|																									
| AuthCodeMisMatch: | Invalid Customer Code|AUTH_CODE_MIS_MATCH|																									
| AuthCodeUsed: | Customer code already been used. Please refresh for another transaction.|AUTH_CODE_USED|																									
| AuthorizationHeaderNotAllowed: | Authorization header is not allowed|AUTHORIZATION_HEADER_NOT_ALLOWED|																									
| BankError: | Bank system error|BANK_ERROR|																									
| BoostMalaysiaNotActive: | Boost Malaysia is not active. Please contact Revenue Monster to activate merchant for boost|BOOST_MALAYSIA_NOT_ACTIVE|																									
| BusinessCategoryNotFound: | Business category not found|BUSINESS_CATEGORY_NOT_FOUND|																									
| BuyerAccountError: | Customer account error|BUYER_ACCOUNT_ERROR|																									
| BuyerAccountInActive: | Customer account is inactive|BUYER_ACCOUNT_IN_ACTIVE|																									
| CampaignNotFound: | Campaign not found|CAMPAIGN_NOT_FOUND|																									
| CannotUpdateSamePhoneNumber:| Cannot update the same phone number|CANNOT_UPDATE_SAME_PHONE_NUMBER|																									
| ChopStampNotActive: | Chop stamp not active|CHOP_STAMP_NOT_ACTIVE|																									
| ChopStampNotFound: | Chop stamp not found|CHOP_STAMP_NOT_FOUND|																									
| ChopStampQuantityExceed: | Reached exceed number of chop stamp card|CHOP_STAMP_QUANTITY_EXCEED|																									
| ClientInvalid: | Invalid client|CLIENT_INVALID|																									
| ClientNoPermission: | Developer application does not have permission to access|CLIENT_NO_PERMISSION|																									
| ClientNotAuthorizeStore: | Developer application not authorize user store|CLIENT_NOT_AUTHORIZE_STORE|																									
| ClientNotFound: | Developer application client not found|CLIENT_NOT_FOUND|																									
| ClientNotSetPublicKey: | Developer application does not set public key|CLIENT_NOT_SET_PUBLIC_KEY|																									
| ClientProductNotSetup: | Developer application product not setup|CLIENT_PRODUCT_NOT_SETUP|																									
| ClientProductSubscribed: | Developer application already subscribed to product|CLIENT_PRODUCT_SUBSCRIBED|																									
| CompanyTypeNotFound: | Company type not found|COMPANY_TYPE_NOT_FOUND|																									
| CustomerReachedTransactionLimit: | Customer reached transaction limit|CUSTOMER_REACHED_TRANSACTION_LIMIT|																									
| DailyPaymentExceeded: | Daily payment limit exceeded|DAILY_PAYMENT_EXCEEDED|																									
| DailyReceiveExceeded: | Daily payment limit exceeded|DAILY_RECEIVED_EXCEEDED|																									
| DefaultStoreDeleteNotAllowed: | Default store not allowed to delete|DEFAULT_STORE_DELETE_NOT_ALLOWED|																									
| DoesNotAllowMultipleBatchProcessing:| Does not allow multiple batch processing|DOES_NOT_ALLOW_MULTIPLE_BATCH_PROCESSING|																									
| DoesNotHaveActiveWallet: | Does not have active wallet. Please contact Revenue Monster to activate wallet|DOES_NOT_HAVE_ACTIVE_WALLET|																									
| EmailDuplicate: | Email address already exists|EMAIL_DUPLICATE|																									
| EmailNotFound: | Email address not found|EMAIL_NOT_FOUND|																									
| ExceededLimit: | Rate limit exceeded|EXCEEDED_LIMIT|																									
| ExceedTimeForReverseTransaction: | Exceed time for transaction to reverse|EXCEED_TIME_FOR_REVERSE_TRANSACTION|																									
| ExpiryInvalid: | Invalid expiry type|EXPIRY_INVALID|																									
| ExpiryMin: | Min expiry day|EXPIRY_MIN|																									
| FailedToReverseOrder: | Failed to reverse order|FAILED_TO_REVERSE_ORDER|																									
| FileNotFound: | File not found|FILE_NOT_FOUND|																									
| GenericTemplateInvalid: | Invalid generic template|GENERIC_TEMPLATE_INVALID|																									
| GrabPayMalaysiaMerchantIDNotSet: | GrabPay Malaysia is not active. Please contact Revenue Monster to activate merchant for GrabPay|GRABPAY_MALAYSIA_MERCHANT_ID_NOT_SET|																									
| GrabPayMalaysiaNotActive: | GrabPay Malaysia is not active. Please contact Revenue Monster to activate merchant for GrabPay|GRABPAY_MALAYSIA_NOT_ACTIVE|																									
| GrantTypeInvalid: | Invalid grant type|GRANT_TYPE_INVALID|																									
| InSufficientCardBalance: | Insuﬃcient customer balance|INSUFFICIENT_CARD_BALANCE|																									
| InSufficientLoyaltyBalance: | Insuffience loyalty balance|INSUFFICIENT_LOYALTY_BALANCE|																									
| InSufficientMerchantBalance: | Insuﬃcient merchant balance|INSUFFICIENT_MERCHANT_BALANCE|																									
| InSufficientPermissionLevel: | Insufficient Permission|INSUFFICIENT_PERMISSION_LEVEL|																									
| InSufficientRefundAmount: | Insufficient refund amount|INSUFFICIENT_REFUND_AMOUNT|																									
| InternalError: | Internal error|INTERNAL_ERROR|																									
| InvalidAgreementVersion: | Invalid Agreement Version| INVALID_AGREEMENT_VERSION |																									
| InvalidAppID: | Invalid parameters|INVALID_APP_ID|																									
| InvalidCharset: | Invalid format|INVALID_CHARSET|																									
| InvalidClient: | Invalid client|INVALID_CLIENT|																									
| InvalidEncryption: | Invalid encryption|INVALID_ENCRYPTION|																									
| InvalidFile: | Invalid file| INVALID_FILE |																									
| InvalidFormat: | Invalid format|INVALID_FORMAT|																									
| InvalidHTTPMethod: | Invalid HTTP Method|INVALID_HTTP_METHOD|																									
| InvalidID: | Invalid id| INVALID_ID |																									
| InvalidImageDimension: | Invalid Image Dimension | INVALID_IMAGE_DIMENSION |																									
| InvalidLoyaltyCreditCode: | Invalid loyalty credit code|INVALID_LOYALTY_CREDIT_CODE|																									
| InvalidOTPCode: | Invalid otp code|INVALID_OTP_CODE|																									
| InvalidParameter: | Invalid parameters|INVALID_PARAMETER|																									
| InvalidParameterID: | Invalid parameter id| INVALID_PARAMETER_ID |																									
| InvalidPaymentSubscriptionMethod: | Invalid payment subscription method|INVALID_PAYMENT_SUBSCRIPTION_METHOD|																									
| InvalidPrivateKey: | Invalid private key|INVALID_PRIVATE_KEY|																									
| InvalidPublicKey: | Invalid public key|INVALID_PUBLIC_KEY|																									
| InvalidRequest: | Invalid request| INVALID_REQUEST |																									
| InvalidRequestSignature: | The request signature is invalid|INVALID_REQUEST_SIGNATURE|																									
| InvalidScope: | Invalid scope|INVALID_SCOPE|																									
| InvalidSignature: | Invalid signature|INVALID_SIGNATURE|																									
| InvalidTerminalToken: | Invalid terminal token|| Please contact Revenue Monster support|INVALID_TERMINAL_TOKEN|																									
| InvalidTimestamp:| Could not authenticate - Timestamp|INVALID_TIMESTAMP|																									
| KeywordDuplicate: | Duplicate keyword|KEYWORD_DUPLICATE|																									
| KeywordKeyInvalid: | Invalid keyword key|KEYWORD_KEY_INVALID|																									
| KeywordNotFound: | Keyword not found|KEYWORD_NOT_FOUND|																									
| ListTemplateInvalid: | Invalid list template|LIST_TEMPLATE_INVALID|																									
| LoyaltyBatchAlreadyGenerateCSV: | Loyalty batch already generate csv|LOYALTY_BATCH_ALREADY_GENERATE_CSV|																									
| LoyaltyBatchAlreadyZip: | Loyalty batch already zip|LOYALTY_BATCH_ALREADY_ZIP|																									
| LoyaltyBirthdayFieldNotRequired: | Birth date field not required|LOYALTY_BIRTHDAY_FIELD_NOT_REQUIRED|																									
| LoyaltyCreditNotEnabled: | Loyalty credit not enable|LOYALTY_CREDIT_NOT_ENABLED|																									
| LoyaltyExpired: | Loyalty point expired|LOYALTY_EXPIRED|																									
| LoyaltyGenerateError: | Error in generating loyalty point|LOYALTY_GENERATE_ERROR|																									
| LoyaltyInsufficient: | Insufficient point|LOYALTY_INSUFFICIENT|																									
| LoyaltyMemberRegistrationTooMany: | length of entity too large | LOYALTY_MEMBER_REGISTRATION_TOO_MANY |																									
| LoyaltyNotCorrectFormat: | Loyalty not correct format|LOYALTY_NOT_CORRECT_FORMAT|																									
| LoyaltyNotFound: | Loyalty not found|LOYALTY_NOT_FOUND|																									
| LoyaltyNotMerchant: | Loyalty not belongs to merchant|LOYALTY_NOT_MERCHANT|																									
| LoyaltyNotSubscribed: | Not subscribed to loyalty|LOYALTY_NOT_SUBSCRIBED|																									
| LoyaltyPointAlreadyRedeemed: | Loyalty point already redeemed|LOYALTY_POINT_ALREADY_REDEEMED|																									
| LoyaltyPointIsProcessing: | Loyalty point is proccessing|LOYALTY_POINT_IS_PROCESSING|																									
| LoyaltyPointMissing: | Loyalty point missing for certain custom id|LOYALTY_POINT_MISSING|																									
| LoyaltyQuantityMax: | Exceeded maximum quantity|LOYALTY_QUANTITY_MAX|																									
| LoyaltySpendingNotAllowed: | Loyalty spending not allowed|LOYALTY_SPENDING_NOT_ALLOWED|																									
| LoyaltySpendingNotFound: | Loyalty spending not found|LOYALTY_SPENDING_NOT_FOUND|																									
| LoyaltySseError: | Error in SSE|LOYALTY_SSE_ERROR|																									
| LoyaltyStatusError: | Error in updating status|LOYALTY_STATUS_ERROR|																									
| MarketPlaceVoucherAlreadyRequested: | Marketplace voucher already requested|MARKET_PLACE_VOUCHER_ALREADY_REQUESTED|																									
| MarketPlaceVoucherExceedQuantity: | Marketplace voucher exceed quantity|MARKET_PLACE_VOUCHER_EXCEED_QUANTITY|																									
| MarketPlaceVoucherNotFound: | Marketplace voucher not found|MARKET_PLACE_VOUCHER_NOT_FOUND|																									
| MasterMerchantCannotSameMerchant: | Master merchant cannot be your own|MASTER_MERCHANT_CANNOT_SAME_MERCHANT|																									
| MasterMerchantNotSubscribe: | Master Merchant not subscribed to this product|MASTER_MERCHANT_NOT_SUBSCRIBE|																									
| MasterMerchantSubscriptionExpired: | Master Merchant subscription expired|MASTER_MERCHANT_SUBSCRIPTION_EXPIRED|																									
| MasterMerchantSubscriptionNotActive: | Master merchant subscription not active|MASTER_MERCHANT_SUBSCRIPTION_NOT_ACTIVE|																									
| MaxValue: | Account update failed: value is too long (maximum is n characters)|MAX_VALUE|																									
| MaxValueMemberTier: | Reach maximum limit for member tier| MAX_VALUE_MEMBER_TIER |																									
| MaxValueRole: | Reach maximum limit for creating Role| MAX_VALUE_ROLE |																									
| MaybankFailToCancelled: | Maybank fail to cancelled|MAYBANK_FAIL_TO_CANCELLED|																									
| MaybankKeyExpired: | Maybank key expired|MAYBANK_KEY_EXPIRED|																									
| MaybankKeyNotFound: | Maybank key not found|MAYBANK_KEY_NOT_FOUND|																									
| MaybankMalaysiaMerchantIDNotSet: | Maybank Malaysia is not active. Please contact Revenue Monster to activate merchant for maybank|MAYBANKA_MALAYSIA_MERCHANT_ID_NOT_SET|																									
| MaybankMalaysiaNotActive: | Maybank Malaysia is not active. Please contact Revenue Monster to activate merchant for maybank|MAYBANK_MALAYSIA_NOT_ACTIVE|																									
| MemberNotFound: | Member not found|MEMBER_NOT_FOUND|																									
| MemberNotMerchant: | Member not belongs to merchant|MEMBER_NOT_MERCHANT|																									
| MemberParentInvalid: | Invalid member parent|MEMBER_PARENT_INVALID|																									
| MemberRegistered: | Member already registered|MEMBER_REGISTERED|																									
| MemberTierMax: | Reached max member tier|MEMBER_TIER_MAX|																									
| MemberTierNotFound: | Member Tier not found|MEMBER_TIER_NOT_FOUND|																									
| MenuInvalid: | Invalid Menu|MENU_INVALID|																									
| MerchantChopStampExpired: | Merchant chop stamp event is expired|MERCHANT_CHOP_STAMP_EXPIRED|																									
| MerchantChopStampNotFound: | Merchant chop stamp event not found|MERCHANT_CHOP_STAMP_NOT_FOUND|																									
| MerchantChopStampNotStarted: | Merchant chop stamp event not started|MERCHANT_CHOP_STAMP_NOT_STARTED|																									
| MerchantGalleryNotFound: | Merchant gallery not found|MERCHANT_GALLERY_NOT_FOUND|																									
| MerchantIDInvalid: | Invalid merchant id|MERCHANT_ID_INVALID|																									
| MerchantInactive: | Merchant account is inactive|MERCHANT_INACTIVE|																									
| MerchantKeyInvalid: | Invalid merchant key|MERCHANT_KEY_INVALID|																									
| MerchantMDRNotSet: | Merchant mdr not set. Please contact Revenue Monster to set.|MERCHANT_MDR_NOT_SET|																									
| MerchantNotActive: | Merchant not active|MERCHANT_NOT_ACTIVE|																									
| MerchantNotFound: | Merchant not found|MERCHANT_NOT_FOUND|																									
| MerchantNotHaveMasterMerchant: | Merchant not have master merchant|MERCHANT_NOT_HAVE_MASTER_MERCHANT|																									
| MerchantNotHavePartner: | Merchant does not have partner|MERCHANT_NOT_HAVE_PARTNER|																									
| MerchantNotSame: | Merchant not same|MERCHANT_NOT_SAME|																									
| MerchantNotSetup: | Merchant not setup|MERCHANT_NOT_SETUP|																									
| MerchantRequestedJoin: | Merchant already requested for join as sub merchant|MERCHANT_REQUESTED_JOIN|																									
| MerchantRequestedJoinNotFound: | Merchant join request not found|MERCHANT_REQUESTED_JOIN_NOT_FOUND|																									
| MerchantSuspended: | Merchant suspended|MERCHANT_SUSPENDED|																									
| MerchantVerified: | Merchant profile is verified|MERCHANT_VERIFIED|																									
| MessageTypeNotFound: | Message type not found|MESSAGE_TYPE_NOT_FUND|																									
| MessengerAccountExists: | Messenger account already exist|MESSENGER_ACCOUNT_EXISTS|																									
| MessengerCodeExpired: | Messenger code expired|MESSENGER_CODE_EXPIRED|																									
| MessengerInvalidToken: | Invalid messenger token|MESSENGER_INVALID_TOKEN|																									
| MessengerMemberDuplicate: | Messenger member registered|MESSENGER_MEMBER_DUPLICATE|																									
| MessengerOwnerAllowConnect: | Only messenger owner allowed to connect|MESSENGER_OWNER_ALLOW_CONNECT|																									
| MessengerOwnerInvalid: | Invalid messenger owner|MESSENGER_OWNER_INVALID|																									
| MessengerPageDuplicate: | Duplicate messenger page|MESSENGER_PAGE_DUPLICATE|																									
| MessengerPageNotFound: | Messenger page not found|MESSENGER_PAGE_NOT_FOUND|																									
| MethodNotAllowed:| Method not allowed|METHOD_NOT_ALLOWED|																									
| MinimumAmountRequired: | Minimum amount should be 10sen|MINIMUM_AMOUNT_REQUIRED|																									
| MinPtsDuplicate: | Min point exists in member tier|Min_PTS_DUPLICATE|																									
| MoneyPacketExpired: | Money packet is expired|MONEY_PACKET_EXPIRED|																									
| MoneyPacketNotFound: | Money packet not found|MONEY_PACKET_NOT_FOUND|																									
| MoneyPacketRedeemed: | Money packet redeemed|MONEY_PACKET_NOT_REDEEMED|																									
| NineGridMerchantNotAllowPayment: | Nine grid not allow to make payment|NINE_GRID_MERCHANT_NOT_ALLOW_PAYMENT|																									
| NoAccess: | This application is not allowed to access|NO_ACCESS|																									
| NoAppID: | Missing parameter|NO_APP_ID|																									
| NoMerchantID: | Missing parameter|NO_MERCHANT_ID|																									
| NoMethod: | Missing parameter|NO_METHOD|																									
| NotAllowDeleteApprovedJoinRequest:| Not allow delete join request|NOT_ALLOW_DELETE_APPROVED_JOIN_REQUEST|																									
| NotAllowLinkProduction: | Not allow link for production|NOT_ALLOW_LINK_PRODUCTION|																									
| NotAllowRefund: | Refunded not allowed|NOT_ALLOW_REFUND|																									
| NotAuth: | Could not authenticate|NOT_AUTH |																									
| NotAuthorizeUserStore: | Not authorize user store|NOT_AUTHORIZE_USER_STORE|																									
| NotMasterMerchant: | Not a master merchant|NOT_MASTER_MERCHANT|																									
| NotMasterMerchantAccount: | Not a master merchant account|NOT_MASTER_MERCHANT_ACCOUNT|																									
| NotNineGridMerchant: | Not a nine grid merchant|NOT_NINER_GRID_MERCHANT|																									
| NotPartnerAccount: | Not a partner account|NOT_PARTNER_ACCOUNT|																									
| NotPermitted: | Not permitted to perform this action.|NOT_PERMITTED|																									
| NotSubscribe: | Merchant not subscribed to this product|NOT_SUBSCRIBE|																									
| NotTerminalTransaction: | Transaction not allowed for different using different terminal|NOT_TERMNAL_TRANSACTION|																									
| NotUserStore: | Not user store|NOT_USER_STORE|																									
| OldPwInvalid: | Invalid old password|OLD_PW_INVALID|																									
| OnlyFreeTierPlugin: | Only free tier plugin|ONLY_FREE_TIER_PLUGIN|																									
| OnlyOwnerAllowForEAgreement: | Only owner allow see e agreement|ONLY_OWNER_ALLOW_FOR_E_AGREEMENT|																									
| OpenIDFail: | Fail to request open ID|OPEN_FAIL|																									
| OrderCancelled: | Order error|ORDDR_CANCELLED|																									
| OrderClosed: | Order error|ORDER_CLOSED|																									
| OrderIDDuplicate: | Order id duplicate|ORDER_ID_DUPLICATE|																									
| OrderNotExist: | Order error|ORDER_NOT_EXIST|																								
| OrderNotPaid: | Order not paid|ORDER_NOT_PAID|																									
| OrderPaid: | Order is paid|ORDER_PAID|																									
| OriginInvalid: | Invalid origin type|ORIGIN_INVALID|																									
| Overload: | Over capacity|OVERLOAD|																									
| OwnerNotAllowedCreate: | Create owner not allowed|OWNER_NOT_ALLOWED_CREATE|																									
| OwnerNotAllowedDelete: | Delete owner is not allowed|OWNER_NOT_ALLOWED_DELETE|																									
| OwnerNotAllowedUpdate: | Update owner is not allowed|OWNER_NOT_ALLOWED_UPDATE|																									
| PageNotFound: | Sorry|| that page does not exist|PAGE_NOT_FOUND|																									
| PartnerMDRNotSet: | Partner mdr is not set. Please contact Revenue Monster to set the partner mdr|PARTNER_MDR_NOT_SET|																									
| PartnerNotFound: | Partner not found|PARTNER_NOT_FOUND|																									
| PartnerNotSame: | Partner not same|PARTNER_NOT_SAME|																									
| PasswordInvalid: | Email address or password is wrong|PASSWORD_IVALID|																									
| PasswordNotStrength: | Password not strength|PASSWORD_NOT_STRENGTH|																									
| PasswordRequired: | Pending customer password|PASSWORD_REQUIRED|																									
| PaymentAmtInvalid: | Invalid amount format|PAYMENT_AMT_INVALID|																									
| PaymentCurrencyInvalid: | Payment currency is invalid|PAYMENT_CURRENCY_INVALID|																									
| PaymentDecimalInvalid: | Invalid decimal|PAYMENT_DECIMAL_INVALID|																									
| PaymentExceedAmountLimitPerTransaction:| Transaction amount is over the limit|PAYMENT_EXCEED_AMOUNT_LIMIT_PER_TRANSACTION|																									
| PaymentExceedAmountPerDay: | Payment exceed amount for per day|PAYMENT_EXCEED_AMOUNT_PER_DAY|																									
| PaymentExceedAmountPerMonth: | Payment exceed amount for per month|PAYMENT_EXCEED_AMOUNT_PER_MONTH|																									
| PaymentExceedNoTransactionPerDay: | Reached exceed number of daily transaction|PAYMENT_EXCEED_NO_TRANSACTION_PER_DAY|																									
| PaymentExceedNoTransactionPerMonth: | Reached exceed number of monthly transaction|PAYMENT_EXCEED_AMOUNT_LIMIT_PER_MONTH|																									
| PaymentFullyRefunded: | Payment already refunded|PAYMENT_FULLY_REFUNDED|																									
| PaymentLimitNotSet: | Payment limit not set. Please contact Revenue Monster to set the limit|PAYMENT_LIMIT_NOT_SET|																									
| PaymentParamInvalid: | Invalid payment params|PAYMENT_PARAM_INVALID|																									
| PaymentRedirect: | Merchant ID and redirect URL not found|PAYMENT_REDIRECT|																									
| PaymentRefundAmountExceedPerDay: | Refund amount transaction exceed then sales amount of the day|PAYMENT_REFUND_AMOUNT_EXCEED_PER_DAY|																									
| PaymentRefunding: | Payment still refunding process|PAYMENT_REFUNDING|																									
| PaymentScanInvalid: | Invalid platform scan|PAYMENT_SCAN_INVALID|																									
| PaymentSubscriptionMethodActive: | Payment method is active|PAYMENT_SUBSCRIPTION_METHOD_ACTIVE|																									
| PaymentTimeout: | Payment timeout|PAYMENT_TIMEOUT|																									
| PaymentUnsupportedCurrencyType: | Unsupported currency type|PAYMENT_UNSUPPORTED_CURRENCY_TYPE|																									
| PhoneDuplicate: | Phone number already exists|PHONE_DUPLICATE|																									
| PinInvalid: | Pin is invalid|PIN_INVALID|																									
| PlatformNotFound: | Platform not found|PLATFORM_NOT_FOUND|																									
| PluginAlreadyInstalled: | Plugin already installed|PLUGIN_ALREADY_INSTALLED|																									
| PluginNotAllowToUpdatePricing: | Plugin not allow to update pricing|PLUGIN_NOT_ALLOW_TO_UPDATE_PRICING|																									
| PluginNotFound: | Plugin not found|PLUGIN_NOT_FOUND|																									
| PluginNotInstalled: | Plugin not installed|PLUGIN_NOT_INSTALLED|																									
| PluginNotVerified: | Plugin not verified|PLUGIN_NOT_VERIFIED|																									
| PluginShouldGreaterThanPreviousVersion:| Plugin version should greater than previous version|PLUGIN_SHOULD_GREATE_THAN_PREVIOUS_VERSION|																									
| PrestoMalaysiaNotActive: | Presto Malaysia is not active. Please contact Revenue Monster to activate merchant for presto|PRESTRO_MALAYSIA_NOT_ACTIVE|																									
| PrestoMDRNotSet: | Presto mdr not set. Please contact Revenue Monster to set.|PRESTO_MDR_NOT_SET|																									
| PrestoMerchantIDNotSet: | Presto merchant id not set. Please contact Revenue Monster to set the merchant id|PRESTO_MERCHANT_ID_NOT_SET|																									
| PrivateKeyReadFile: | Cannot read private key|PRIVATE_KEY_READ_FILE|																									
| ProductSubscriptionActive: | Product subscription is active|PRODUCT_SUBSCRIPTION_ACTIVE|																									
| QRInvalid: | Invalid QR code|QR_INVALID|																									
| QRRedeemed: | QR code redeemed|QR_REDEEMED|																									
| QuickPayNotRegistered: | User is not registered with Quick Pay|QUICK_PAY_NOT_REGISTERED|																									
| ReconciliationNotFound: | Reconciliation record not found|RECONCILIATION_NOT_FOUND|																									
| RedemptionMerchantInvalid: | Invalid redemption rule merchant|REDEMPTION_MERCHANT_INVALID|																									
| RedemptionParentInvalid: | Invalid redemption rule parent key|REDEMTION_PARENT_INVALID|																									
| RedemptionRuleKeyInvalid: | Invalid redemption rule key|REDEMPTION_RULE_KEY_FOUND|																									
| RedemptionRuleLimitReached: | Reached the voucher limit per member|REDEMPTION_RULE_LIMIT_REACHED|																									
| RedemptionRuleNotFound: | Redemption rule not found|REDEMPTION_RULE_NOT_FOUND|																									
| RefundAmtNotSameAsTotalAmount: | Refund amount not same as total amount|REFUND_AMT_NOT_SAME_AS_TOTAL_AMOUNT|																									
| RefundAmtNotSameAsTransaction: | Refund amount not same as transaction amount|REFUND_AMT_NOT_SAME_AS_TRANSACTION|																									
| RefundPaymentNotFound: | Refund payment not found|REFUND_PAYMENT_NOT_FOUND|																									
| RefundPinInvalid: | Wrong pin number|REFUND_PIN_INVALID|																									
| RefundUserNotFound: | Refund user not found|REFUND_USER_NOT_FOUND|																									
| ReportNotFound: | Report does not exist|REPORT_NOT_FOUND|																									
| ResetKeyInvalid: | Invalid password reset key|RESET_KEY_INVALID|																									
| ResetLinkExpired: | Password reset link expired|RESET_LINK_EXPIRED|																									
| ResourceGone: | Resource no longer exists | RESOURCE_GONE |																									
| RoleKeyInvalid:| Invalid role key| ROLE_KEY_INVALID |																									
| RoleNotFound: | Role not found| ROLE_NOT_FOUND |																									
| ScopeNotFound: | Scope not found| SCOPE_NOT_FOUND |																									
| ShouldHaveIndexFile: | Should have index.html file|SHOULD_HAVE_INDEX_FILE|																									
| SignatureInvalid: | Invalid signature|SIGNATURE_INVALID|																									
| SmsFail: | Failed to send SMS|SMS_FAIL|																									
| SPAM: | Suspicious activity|SPAM|																									
| SpendingDuplicate: | Spending loyalty set|SPENDING_DUPLICATE|																									
| SpendingNotFound: | No spending loyalty|SPENDING_NOT_FOUND|																									
| SSLRequired: | SSL is required|SSL_REQUIRED|																									
| StoreHasUser: | The store has user|STORE_NOT_USER|																									
| StoreIDInvalid: | Invalid store ID|STORE_ID_INVALID|																									
| StoreInvalidFormat: | Store format invalid|STORE_INVALID_FORMAT|																									
| StoreKeyInvalid: | Invalid store key|STORE_KEY_INVALID|																									
| StoreMaximum: | Maximum store allowed to create is 10|STORE_MAXIMUM|																									
| StoreNotFound: | Store not found|STORE_NOT_FOUND|																									
| StoreNotSet: | Store not set|STORE_NOT_SET|																									
| SubMerchantDoesNotAllowedLoyalty: | Sub merchant not allowed to access loyalty|SUB_MERCHANT_DOES_NOT_ALLOWED_LOYALTY|																									
| SubscriptionExists: | Merchant already subscribed to this product.|SUBSCRIPTION_EXISTS|																									
| SubscriptionExpired: | Merchant subscription expired|SUBSCRIPTION_EXPIRED|																									
| SubscriptionNotActive: | You have not subscribed to this product|SUBSCRIPTION_NOT_ACTIVE|																									
| SubscriptionNotFound: | Subscription not found|SUBSCRIPTION_NOT_FOUND|																									
| SystemError: | System timed out|SYSTEM_ERROR|																									
| TacInvalid: | Invalid TAC code|TAC_INVALID|																									
| TacLimit: | TAC code limit has reached|TAC_LIMIT|																									
| TacRequired: | User TAC code is required|TAC_REQUIRED|																									
| TacSent: | TAC code has sent|TAC_SENT|																									
| TemplateBodyInvalid: | Invalid template body|TEMPLATE_BODY_INVALID|																									
| TemplateKeyInvalid: | Invalid template key|TEMPLATE_KEY_INVALID|																									
| TemplateKeywordDuplicate: | Invalid template keyword|TEMPLATE_KEYWORD_DUPLICATE|																									
| TemplateMessageDraft: | Draft template message|TEMPLATE_MESSAGE_DRAFT|																									
| TemplateMessageDuplicate: | Invalid template message|TEMPLATE_MESSAGE_DUPLICATE|																									
| TemplateNotFound: | Template not found|TEMPLATE_NOT_FOUND|																									
| TerminalAlreadyRegistered: | Terminal already registered|TERMINAL_ALREADY_REGISTERED|																									
| TerminalInActive: | Terminal is not active|TERMINAL_INACTIVE|																									
| TerminalNoPermission: | Terminal does not have permission to access|TERMINAL_NO_PERMISSION|																									
| TerminalNotFound: | Terminal not found|TERMINAL_NOT_FOUND|																									
| TerminalRefundTokenInvalid: | Terminal refund token invalid|TERMINAL_REFUND_TOKEN_INVALID|																									
| TerminalSerialAlreadyExist:| Terminal serial already exist|TERMINAL_SERIAL_ALREADY_EXIST|																									
| TerminalSerialNotFound: | Terminal serial not found|TERMINAL_SERIAL_NOT_FOUND|																									
| TNGMalaysiaNotActive: | TNG Malaysia is not active. Please contact Revenue Monster to activate merchant for tng|TNG_MALAYSIA_NOT_ACTIVE|																									
| TokenExpired: | Invalid or expired token|TOKEN_EXPIRED|																									
| TokenInvalid: | Unable to verify your credentials|TOKEN_INVALID|																									
| TokenSuspended: | Access token suspended|TOKEN_SUSPENDED|																									
| TransactionDuplicate: | Duplicate order number|TRANSACTION_DUPLICATE|																									
| TransactionExpired: | Transaction is expired|TRANSACTION_EXPIRED|																									
| TransactionNotFound: | No payment transaction|TRANSACTION_NOT_FOUND|																									
| TransactionPaid: | Transaction already paid|TRANSACTION_PAID|																									
| TransactionQRCodeNotFound: | Transaction qr code not found|TRANSACTION_QR_CODE_NOT_FOUND|																									
| TransactionStatusFailed: | Payment transaction status failed|TRANSACTION_STATUS_FAILED|																									
| TransactionStatusNotInProccess: | Transaction status not in process|TRANSACTION_STATUS_NOT_IN_PROCCESS|																									
| TransactionStatusNotSuccess: | Transaction status not success|TRANSACTIN_STATUS_NOT_SUCCESS|																									
| Unauthorized: | Unauthorized|UNAUTHORIZED|																									
| UniqueCodeDuplicate: | Duplicate unique code|UNIQUE_CODE_DUPLICATE|																									
| UniqueCodeEmpty: | Empty unique code|UNIQUE_CODE_EMPTY|																									
| UniqueCodeInvalid: | Invalid unique code|UNIQUE_CODE_INVALID|																									
| UnSupportedJSAPIMethod: | Unsupported method for jsapi|UNSUPPORTED_JSAPI_METHOD|																									
| UnSupportedJSAPIRegion: | Unsupported region for jsapi|UNSUPPORTED_JSAPI_REGION|																									
| UnSupportedMethodPaymentRefund: | Unsupported method payment refund|UNSUPPORTED_METHOD_PAYMENT_REFUND|																									
| UnSupportedMethodReverse: | Unsupported method for reverse|UNSUPPORTED_METHOD_REVERSE|																									
| UserAlreadyRegistered: | User already registered|USER_ALREADY_REGISTERED|																									
| UserCannotUpdateOwnAccount: | User cannot update own account|USER_CANNOT_UPDATE_OWN_ACCOUNT|																									
| UserCreateFail: | Unauthorized to create user|USER_CREATE_FAIL|																									
| UserDeleteFail: | Unauthorized to delete user|USER_DELETE_FAIL|																									
| UserDeviceNotFound: | User device not found|USER_DEVICE_NOT_FOUND|																									
| UserDuplicate: | User account already exist|USER_DUPLICATE|																									
| UserKeyInvalid: | Invalid user key|USER_KEY_INVALID|																									
| UserNoPermission: | User does not have permission to access|USER_NO_PERMISSION|																									
| UserNotActive: | User not active|USR_NOT_ACTIVE|																									
| UserNotCreateAccount: | User not create account|USER_NOT_CREATE_ACCOUNT|																									
| UserNotFound: | User not found|USER_NOT_FOUND|																									
| UserPinCodeInvalid: | Invalid user pin code|USER_PIN_CODE_INVALID|																									
| UserProfileNotFound: | User login profile not found|USER_PROFILE_NOT_FOUND|																									
| UserSuspended: | User has been suspended|USER_SUSPENDED|																									
| ValidationError: | Validations error| VALIDATION_ERROR |																									
| VEmailNotFound: | User verification email not found|V_EMAIL_NOT_FOUND|																									
| VerificationCodeAlreadyRequested: | Verification code already requested | VERIFICATION_CODE_ALREADY_REQUESTED |																									
| VerificationCodeInvalid: | Verification code invalid | VERIFICATION_CODE_INVALID |																									
| VerificationCodeReachDailyLimit: | Verification code request reach daily limit | VERIFICATION_CODE_REACH_DAILY_LIMIT |																									
| VerificationTokenInvalid: | Invalid verification token| VERIFICATION_TOKEN_INVALID |																									
| VerificationTypeNotFound: | Verification code type not found | VERIFICATION_TYPE_NOT_FOUND |																									
| VLinkExpired: | Verification link is expired|V_LINK_EXPIRED|																									
| VoucherBatchExpired: | Voucher batch expired|VOUCHER_BATCH_EXPIRED|																									
| VoucherBatchKeyInvalid: | Voucher batch key is invalid|VOUCHER_BATCH_KEY_INVALID|																									
| VoucherBatchNotEnoughQuantity: | Voucher batch not enough quantity|VOUCHER_BATCH_NOT_ENOUGH_QUANTITY|																									
| VoucherBatchNotFound: | Voucher batch not found|VOUCHER_BATCH_NOT_FOUND|																									
| VoucherComboExpired: | Voucher combo expired|VOUCHER_COMBO_EXPIRED|																									
| VoucherComboNotEnoughQuantity: | Voucher combo not enough quantity|VOUCHER_COMBO_NOT_ENOUGH_QUANTITY|																									
| VoucherComboNotFound: | Voucher combo not found|VOUCHER_COMBO_NOT_FOUND|																									
| VoucherInsufficient: | Insufficient voucher batch|VOUCHER_INSUFFICIENT|																									
| VoucherNotAllowVoid: | Voucher not allow to void|VOUCHER_NOT_ALLOW_VOID|																									
| VoucherNotFound: | Voucher not found|VOUCHER_NOT_FOUND|																									
| VoucherNotMerchant: | Voucher is not belongs to merchant|VOUCHER__NOT_MERCHANT|																									
| VoucherNotMinimumAmount: | Voucher does not meet minimum amount|VOUCHER__NOT_MINIMUM_AMOUNT|																									
| VoucherNotRedeemed: | Voucher is not redeemed|VOUCHER_NOT_REDEMMED|																									
| VoucherOwnerInvalid: | Voucher not owned|VOUCHER_OWNER_INVALID|																									
| VoucherRedeemed: | Voucher redeemed|VOUCHER_REDEEMED|																									
| VoucherRedeemedInvalid: | Invalid direct redeem|VOUCHER_REDEEMED_INVALID|																									
| VoucherRedeemMax: | Max redeem voucher|VOUCHER_REDEEM_MAX|																									
| VoucherSoldOut: | Voucher sold out|VOUCHER_SOLD_OUT|																									
| WeChatAccountDuplicate: | WeChat account already exists|WECHAT_ACCOUNT_DUPLICATE|																									
| WeChatPageDuplicate: | Duplicate wechat page|WECHAT_PAGE_DUPLICATE|																									
| WeChatPageInvalid: | Invalid wechat page|WECHAT_PAGE_INVALID|																									
| WeChatPageNotFound: | Wechat page not found|WECHAT_PAGE_NOT_FOUND|																									
| WeChatPayChinaMDRNotSet: | WeChatPay China mdr not set. Please contact Revenue Monster to set.|WECHATPAY_CHINA_MDR_NOT_SET|																									
| WeChatPayChinaMerchantIDNotSet: | WeChatPay China merchant id not set. Please contact Revenue Monster to set the merchant id|WECHATPAY_CHINA_MERCHANT_ID_NOT_SET|																									
| WeChatPayChinaNotActive: | WeChatPay China is not active. Please contact Revenue Monster to activate merchant for wechat pay|WECHATPAY_CHINA_NOT_ACTIVE|																									
| WeChatPayClientDuplicate: | Wechat pay client duplicate|WECHATPAY_CLIENT_DUPLICATE|																									
| WeChatPayClientNotFound: | Wechat pay client not found|WECHATPAY_CLIENT_NOT_FOUND|																									
| WeChatPayMalaysiaMDRNotSet: | WeChatPay Malaysia mdr not set. Please contact Revenue Monster to set.|WECHATPAY_MALAYSIA_MDR_NOT_SET|																									
| WeChatPayMalaysiaMerchantIDNotSet: | WeChatPay Malaysia merchant id not set. Please contact Revenue Monster to set the merchant id|WECHATPAY_MALAYSIA_MERCHANT_ID_NOT_SET|																									
| WeChatPayMalaysiaNotActive: | WeChatPay Malaysia is not active. Please contact Revenue Monster to activate merchant for wechat pay|WECHATPAY_MALAYSIA_NOT_ACTIVE|																									
| WeChatPhoneInvalid: | Invalid wechat phone number|WECHAT_PHONE_INVALID|																									
| WeChatTemplateMessageFailed: | WeChat template message failed|WECHAT_TEMPLATE_MESSAGE_FAILED|																									
| TooManyRequestPerSecond: | Reached maximum request limit per second| TOO_MANY_REQUEST_PER_SECOND |						

##Appedix: Version Control

- 11/06/2018: Updated RSA keys generator, improved documentation description in RM OAuth, updated Signature Debugger, updated each endpoint structure.
- 01/07/2018: Added "Payment Transaction QR Code" endpoint(s).
- 16/07/2018: Refactor documentation for Signature Algorithm.
- 30/07/2018: Removed `isDebug` parameter in all API calls. Added `terminalId` for payment API.
