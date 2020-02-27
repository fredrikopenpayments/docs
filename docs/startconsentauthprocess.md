---
id: startconsentauthprocess
title: Start Consent Authorisation Process
sidebar_label: Start Consent Authorisation Process
---
```javascript
curl -X POST
    [API_HOST]/psd2/consent/v1/consents/[CONSENT_ID]/authorisations
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'PSU-IP-Address: [PSU_IP_Address]'
    -H 'X-BicFi: [BICFI]'
    -H 'X-Request-ID: [GUID]'
```

Note that this call does not need a body despite being a `POST`.

### Headers

See Create consent.

### Path parameter

- `CONSENT_ID`

### Response
```javascript
{
    "authorisationId": "[CONSENT_AUTH_ID]",
    "scaMethods": [
        {
            "authenticationType": "PUSH_OTP",
            "authenticationMethodId": "[AUTHENTICATION_METHOD_ID]"
        }
    ],
    "_links": {
        "scaStatus": {
            "href": "/psd2/consent/v1/consents/[CONSENT_ID]/authorisations/[CONSENT_AUTH_ID]"
        },
        "selectAuthenticationMethod": {
            "href": "/psd2/consent/v1/consents/[CONSENT_ID]/authorisations/[CONSENT_AUTH_ID]"
        }
    },
    "scaStatus": "started"
}
```

### Response headers

- `ASPSP-SCA-Approach` - see below for different values.
- `X-Request-ID`