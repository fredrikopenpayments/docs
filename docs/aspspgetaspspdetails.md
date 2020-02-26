---
id: aspspgetaspspdetails
title: Get ASPSP Details
sidebar_label: Get ASPSP Details
---
With this resource you can get the details about the ASPSP and supported [payment products](paymentproducts.md).

```javascript
curl -X GET
    [API_HOST]/psd2/aspspinformation/v1/aspsps/[BICFI]
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'X-Request-ID: [GUID]'
```

### Path parameter
- `BICFI` ASPSP identifier

You can get bank details by entering the BicFi code. Get the BicFi code from the [Get ASPSP List](aspspgetaspsplist.md) resource.

### Response
```javascript
{
    "city": "Stockholm",
    "country": "Sweden",
    "postalCode": "106 40",
    "streetAddress": "Kungsträdgårdsgatan 8",
    "companyNumber": "502032-9081",
    "phone": "+46-771 365 365",
    "websiteUrl": "https://seb.se/",
    "globalPaymentProducts": [
        "sepa-credit-transfers",
        "domestic",
        "international"
    ],
    "paymentProducts": [
        "swedish-domestic-private-own-accounts-transfers",
        "swedish-domestic-private-bankgiros",
        "swedish-domestic-private-plusgiros",
        "high-value-credit-transfers",
        "se-domestic-credit-transfers"
    ],
    "supportedAuthorizationMethods": [
        {
            "name": "OAuth2",
            "uri": "https://auth.sandbox.openbankingplatform.com/.well-known/openid-configuration"
        }
    ],
    "bicFi": "ESSESESS",
    "name": "Skandinaviska Enskilda Banken AB ",
    "logoUrl": "https://opeopenbanking.blob.core.windows.net/images/ESSESESS.jpg"
}
```
The ``companyNumber`` is equivalent to the organisation number. 

The ``globalPaymentProducts`` are supported by Open Payments for all banks. For more information about the supported payment products, see [payment products](paymentproducts.md).

Note! The ``paymentProducts`` are supported, but needs to be configured accourding to the bank´s documentation.

The ``supportedAuthorizationMethods`` refers to the Open Payments authorisation method and environment.