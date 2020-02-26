---
id: pisauthsubres
title: Get Payment Initiation Authorisation Sub-Resources
sidebar_label: Get Payment Initiation Authorisation Sub-Resources
---
    curl -X GET
        [API_HOST]/psd2/paymentinitiation/v1/payments/[PAYMENT_PRODUCT]/[PAYMENT_ID]/authorisations
        -H 'Authorization: Bearer [ACCESS_TOKEN]'
        -H 'PSU-IP-Address: [PSU_IP_ADDRESS]'
        -H 'X-BicFi: [BICFI]'
        -H 'X-Request-ID: [GUID]'

### Headers

See [Create Payment Initiation](#create-payment-initiation)

### Path parameters

`PAYMENT_ID` that was returned from the initiation request.

### Response
```javascript
{
    "authorisationIds": [
        "[PAYMENT_AUTH_ID"
    ]
}
```

### Response headers

- `X-Request-ID`