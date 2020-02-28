---
id: updatepsudataforconsent
title: Update PSU Data for Consent
sidebar_label: Update PSU Data for Consent
---
```javascript
curl -X PUT
    [API_HOST]/psd2/consent/v1/consents/[CONSENT_ID]/authorisations/[CONSENT_AUTH_ID]
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'PSU-IP-Address: [PSU_IP_Address]'
    -H 'X-BicFi: [BICFI]'
    -H 'X-Request-ID: [GUID]'
    -d '{
        "authenticationMethodId": "[AUTHENTICATION_METHOD_ID]"
    }'
```

### Headers

- `PSU-IP-Address` is the IP address of the end user.
- `X-BicFi` the BICFI for the user's ASPSP. Find it in [the ASPSP API](aspsp.md).
- `X-Request-ID` used to verify that the response matches the request.

### Path parameter

Get the `CONSENT_ID` from the [Get consent](getconsent.md) resource.

Get the `CONSENT_AUTH_ID`from the [Start consent authorisation process](startconsentauthprocess.md) resource.

### Response headers

- `ASPSP-SCA-Approach` see below for different values.
- `X-Request-ID`

### Response
```javascript
{
    "chosenScaMethod": {
        "authenticationType": "PUSH_OTP",
        "authenticationMethodId": "[AUTHENTICATION_METHOD_ID]"
    },
    "_links": {
        "scaStatus": {
            "href": "/psd2/consent/v1/consents/[CONSENT_ID]/authorisations/[CONSENT_AUTH_ID]"
        },
        "scaOAuth": {
            "href": "[AUTH_HOST]/connect/authorize?client_id=[CLIENT_ID]&scope=accountinformation&response_type=code&redirect_uri=[TPP_REDIRECT_URI]&state=[TPP_STATE]&acr_values=idp:[BICFI]%20consentId:[CONSENT_ID]%20consentAuthorisationId:[CONSENT_AUTH_ID]"
        }
    },
    "psuMessage": "Please confirm with your bank app",
    "scaStatus": "scaMethodSelected"
}
```

### Test procedure

If the ASPSP uses OAuth:

This endpoint returns an OAuth authorize URL in the `scoOAuth` field. 
1. Replace all the bracketed fields with real values. In your code you will only have to replace the two TPP values:
    - `TPP_REDIRECT_URI` - the URL to redirect to after auth is completed.
    - `TPP_STATE` can be anything the TPP wants.
    - `BICIFI`
1. Run in a browser. In this case you will get to a page at the ESSESESS sandbox. It may differ for different banks.
1.  In the page you get to you can use one of the following fake personal numbers:
    - 9311219639
    - 9311219589
    - 8811215477
    - 8811212862
    - 8311211356

    When you submit the data you will be redirected to the `[TPP_REDIRECT_URI]`. On this URI a `code` param will be added. 
1. Use this `code` in the subsequent call when getting the account information token and call the OAuth token endpoint to finalize consent flow.

This is the post:

    curl -X POST
        [AUTH_HOST]/connect/token
        -H 'Content-Type: application/x-www-form-urlencoded'
        -H 'X-ConsentAuthorisationId: [CONSENT_AUTH_ID]'
        -H 'X-ConsentId: [CONSENT_ID]'
        -d 'client_id=[CLIENT_ID]&client_secret=[CLIENT_SECRET]&code=[CODE]&redirect_uri=[TPP_REDIRECT_URI]&grant_type=authorization_code'

Now you are ready to call the account service. For more information, see [How to use AIS](ais.md).