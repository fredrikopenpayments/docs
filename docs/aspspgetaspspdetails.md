---
id: aspspgetaspspdetails
title: Get ASPSP Details
sidebar_label: Get ASPSP Details
---

```javascript
curl -X GET
    [API_HOST]/psd2/aspspinformation/v1/aspsps/[BICFI]
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'X-Request-ID: [GUID]'
```

### Path parameter

- `BICFI` ASPSP identifier. It can be known upfront or it can be picked from the previous response.

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

This result contains contact details for the bank and information about how to access its services through Open Payments API.

The list of **global payment products** is generic payments products that we support for all banks (where it makes sense). In this case the swedish bank SEB has support for domestic payments internally in Sweden and sepa payments on the European market. When using these we have a unified API for payments that work across banks. If you want a no hassle experience where the API towards us always is the same - this is the products to use.

The list of **payment products** is specifically for the bank at hand. When using one of these you have to send payment information in a format the bank will accept. 

Read more about the [payment initiation](pis.md) API.