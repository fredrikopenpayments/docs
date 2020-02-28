---
id: startconsentauthprocess
title: Start Consent Authorisation Process
sidebar_label: Start Consent Authorisation Process
---
This endpoint starts the consent authorisation process.

```javascript
curl -X POST
    [API_HOST]/psd2/consent/v1/consents/[CONSENT_ID]/authorisations
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'PSU-IP-Address: [PSU_IP_Address]'
    -H 'X-BicFi: [BICFI]'
    -H 'X-Request-ID: [GUID]'
```

Note! This call does not need a body (despite being a `POST`).

### Headers
- `PSU-IP-Address` is the IP address of the end user.
- `X-BicFi` the BICFI for the user's ASPSP. Find it in [the ASPSP API](/en/openpayments-NextGenPSD2-1.3.3.html#tag/ASPSP-Information-Service-(ASPSPIS)).
- `X-Request-ID` used to verify that the response matches the request.

### Path parameter

Get the `CONSENT_ID` from the [Get consent](getconsent.md) resource.

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

- `X-Request-ID`
- `ASPSP-SCA-Approach` - This is a response header that describes how to proceed with authentication and has one of the following values:
* EMBEDDED
* DECOUPLED
* REDIRECT

    For more information about the SCA approaches, see [SCA approaches]("sca.md").