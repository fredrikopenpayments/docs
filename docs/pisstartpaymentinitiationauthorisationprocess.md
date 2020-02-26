---
id: pisstartpaymentinitiationauthorisationprocess
title: Start Payment Initiation Authorisation Process
sidebar_label: Start Payment Initiation Authorisation Process
---
```javascript
curl -X POST
    [API_HOST]/psd2/paymentinitiation/v1/payments/[PAYMENT_PRODUCT]/[PAYMENT_ID]/authorisations
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'PSU-IP-Address: [PSU_IP_ADDRESS]'
    -H 'X-BicFi: [BICFI]'
    -H 'X-Request-ID: [GUID]'
    -H 'Content-Type: application/json'
```

Note that this call does not need a body.

### Headers

See [Create Payment Initiation](#create-payment-initiation)

### Path parameters

`PAYMENT_ID` that was returned from the initiation request.

### Response
```javascript
{
    "authorisationId": "[PAYMENT_AUTH_ID]",
    "scaStatus": "received",
    "scaMethods": [
        {
            "authenticationType": "PUSH_OTP",
            "authenticationMethodId": "[AUTHENTICATION_METHOD_ID]"
        }
    ],
    "_links": {
        "authoriseTransaction": {
            "href": "/psd2/paymentinitiation/v1/payments/[PAYMENT_PRODUCT]/[PAYMENT_ID]/authorisations/[PAYMENT_AUTH_ID]"
        }
    }
}
```

### Response headers

- `ASPSP-SCA-Approach` - see [below](#aspsp\-sca\-approach) for different values.
- `X-Request-ID`