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

- `PSU-IP-Address` is the IP address of the end user.
- `X-BicFi` the BICFI for the user's ASPSP. Find it in [the ASPSP API](/en/openpayments-NextGenPSD2-1.3.3.html#tag/ASPSP-Information-Service-(ASPSPIS)).
- `X-Request-ID` used to verify that the response matches the request.

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